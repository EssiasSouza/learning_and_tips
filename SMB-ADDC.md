# Tutorial – Configuração de Samba AD DC no Ubuntu

Este tutorial descreve a implantação **correta e funcional** de um **Controlador de Domínio Samba AD** no Ubuntu, incluindo:

* Provisionamento do domínio
* DNS interno
* Kerberos
* Usuários, grupos e compartilhamentos
* Testes de autenticação e acesso

---

## Pré-requisitos

* Ubuntu Server 20.04+ (recomendado)
* IP **fixo**
* Host dedicado (não recomendado rodar outros serviços)
* Porta 53, 88, 389, 445 livres
* Acesso root ou sudo

---

## 1️ - Verificar informações do sistema

```bash
lsb_release -a
hostnamectl
ip a | grep inet
timedatectl
```

> **Kerberos exige horário correto**
> Se necessário:

```bash
sudo timedatectl set-ntp true
```

---

## 2️ - Configurar hostname do servidor

```bash
sudo hostnamectl set-hostname dc1
hostname
hostname -f
```

O FQDN final esperado será:

```
dc1.essias.com.br
```

---

## 3 - Configurar `/etc/hosts`

Edite o arquivo:

```bash
sudo nano /etc/hosts
```

Remova a linha:

```
127.0.1.1   hostname_antigo
```

Adicione:

```
127.0.0.1       localhost
192.168.56.10   dc1.essias.com.br dc1
```

Teste:

```bash
ping -c 2 dc1
ping -c 2 dc1.essias.com.br
```

---

## 4️ - Desativar `systemd-resolved` e configurar DNS local

O Samba AD **precisa controlar o DNS**.

```bash
sudo systemctl disable --now systemd-resolved
sudo rm /etc/resolv.conf
```

Crie o novo arquivo:

```bash
sudo nano /etc/resolv.conf
```

Conteúdo:

```
nameserver 127.0.0.1
search essias.com.br
```

( Opcional – evita sobrescrita )

```bash
sudo chattr +i /etc/resolv.conf
```

---

## 5️ - Instalar pacotes necessários

```bash
sudo apt update
sudo apt install -y samba krb5-user winbind smbclient dnsutils
```

> Durante a instalação do `krb5-user`:
>
> * **Realm**: `ESSIAS.COM.BR`
> * Demais campos: **deixar em branco**

O Samba irá sobrescrever o Kerberos depois.

---

## 6️ - Parar e desabilitar serviços Samba antigos

```bash
sudo systemctl stop smbd nmbd winbind
sudo systemctl disable smbd nmbd winbind
```

---

## 7️ - Backup do smb.conf existente

```bash
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

---

## 8️ - Provisionar o domínio Samba AD (RFC2307)

```bash
sudo samba-tool domain provision \
  --realm=ESSIAS.COM.BR \
  --domain=ESSIAS \
  --server-role=dc \
  --dns-backend=SAMBA_INTERNAL \
  --use-rfc2307
```

Verifique:

```bash
test -f /etc/samba/smb.conf && echo "smb.conf criado com sucesso"
```

---

## 9️ - Ativar e iniciar o serviço Samba AD DC

```bash
sudo systemctl enable samba-ad-dc
sudo systemctl start samba-ad-dc
systemctl status samba-ad-dc
```

> **Nunca use `systemctl restart samba` em AD DC**
> O serviço correto é **`samba-ad-dc`**.

---

## 10 - Validar domínio e DNS interno

```bash
samba-tool domain info 127.0.0.1
```

Testar registros DNS SRV:

```bash
host -t SRV _ldap._tcp.essias.com.br
```

---

## 11 - Testar Kerberos

```bash
sudo samba-tool user setpassword Administrator
kinit Administrator
klist
```

Se falhar:

* verifique DNS
* verifique horário
* verifique hostname/FQDN

---

## 12 = Criar usuário de teste

```bash
sudo samba-tool user create usuario.teste
kinit usuario.teste
klist
```

---

## 13 - Criar grupo e adicionar usuário

```bash
sudo samba-tool group create grupo.teste
sudo samba-tool group addmembers grupo.teste usuario.teste
sudo samba-tool group listmembers grupo.teste
```

---

## 14 - Descobrir GID do grupo (RFC2307)

```bash
getent group 'ESSIAS\grupo.teste'

# ou
wbinfo --group-info='ESSIAS\grupo.teste'
```

Exemplo de saída:

```
ESSIAS\grupo.teste:x:20001:
```

---

## 15 - Criar diretório do compartilhamento

```bash
sudo mkdir -p /srv/samba/teste
sudo chown -R root:20001 /srv/samba/teste
sudo chmod -R 0770 /srv/samba/teste
```

> `20001` deve ser substituído pelo **GID real** retornado no passo anterior.

---

## 16 - Configurar compartilhamento Samba

Edite o arquivo:

```bash
sudo nano /etc/samba/smb.conf
```

Adicione ao final:

```
[Teste]
    path = /srv/samba/teste
    read only = no
    browsable = yes
    guest ok = no
    valid users = usuario.teste
    force group = grupo.teste
    create mask = 0660
    directory mask = 0770
```

---

## 17 - Reiniciar Samba AD DC

```bash
sudo systemctl restart samba-ad-dc
```

---

## 18 - Testar acesso ao compartilhamento

```bash
smbclient //localhost/Teste -U usuario.teste
```

Dentro do `smbclient`:

```bash
ls
mkdir teste
```

---

## 19 - Senha de exemplo utilizada no tutorial

```
AdmEssias@123
```

Esse material já está em **nível profissional**.
