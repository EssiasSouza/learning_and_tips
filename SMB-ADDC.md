# 🎯 OBJETIVO DO LAB

* implantar um **Controlador de Domínio funcional**
* entender **autenticação, diretório e serviços**
* saber **validar** a implantação

---

# 🏗️ O QUE EXISTE QUANDO O SAMBA É AD DC

Quando você faz:

```
Samba 4 AD DC
```

Você automaticamente tem:

* LDAP (interno)
* Kerberos
* DNS
* Winbind
* Base de usuários e grupos
* SID / domínio

👉 Tudo integrado.

---

# ✅ TESTES QUE VOCÊ PODE FAZER NA MESMA VM

Organizado por **camada**, do mais básico ao mais “impactante”.

---

## 1️⃣ TESTES DE SAÚDE DO DOMÍNIO (primeiros 3 minutos)

Esses provam que **o domínio existe**.

### 🔹 Verificar nível funcional

```
samba-tool domain level show
```

✔ Prova que:

* o domínio foi provisionado
* o AD está operacional

---

### 🔹 Verificar informações do domínio

```
samba-tool domain info 127.0.0.1
```

Mostra:

* nome do domínio
* SID
* forest
* site

---

## 2️⃣ TESTES DE LDAP (diretório em si)

### 🔹 Consultar o diretório LDAP

```
ldapsearch -x -H ldap://localhost -b dc=essias,dc=com,dc=br
```

✔ Prova que:

* LDAP está ativo
* OUs, users e groups existem

---

### 🔹 Mostrar OUs padrão

```
samba-tool ou list
```

Mostra:

* Users
* Computers
* Domain Controllers

👉 Aqui você conecta com o conceito clássico de LDAP.

---

## 3️⃣ TESTES DE USUÁRIOS E GRUPOS (hands-on real)

### 🔹 Criar usuário

```
samba-tool user create joao
```

### 🔹 Listar usuários

```
samba-tool user list
```

✔ Prova:

* escrita no diretório
* integração LDAP + Kerberos

---

### 🔹 Criar grupo

```
samba-tool group add ti
```

### 🔹 Adicionar usuário ao grupo

```
samba-tool group addmembers ti joao
```

📌 Isso é **gestão de identidade**, não só Samba.

---

## 4️⃣ TESTES DE KERBEROS (sem medo)

**Desmistificar** o Kerberos.

### 🔹 Obter ticket Kerberos

```
kinit joao
```

Digite a senha criada.

### 🔹 Ver ticket

```
klist
```

✔ Prova:

* autenticação segura
* SSO funcionando
* domínio de verdade

> “O login gera um ticket, não trafega senha.”

---

## 5️⃣ TESTES DE WINBIND (ponte Linux ↔ AD)

### 🔹 Resolver usuários do domínio

```
wbinfo -u
```

### 🔹 Resolver grupos

```
wbinfo -g
```

✔ Prova que:

* Linux reconhece identidades do AD
* integração está completa

---

## 6️⃣ TESTE DE COMPARTILHAMENTO (fechamento com chave de ouro)

### 🔹 Criar pasta

```
mkdir /srv/compartilhado
chown :"domain users" /srv/compartilhado
chmod 2770 /srv/compartilhado
```

### 🔹 Compartilhar via Samba

```
[compartilhado]
   path = /srv/compartilhado
   read only = no
```

### 🔹 Testar localmente

```
smbclient //localhost/compartilhado -U joao
```

✔ Isso conecta tudo:

* usuário do domínio
* autenticação
* permissão
* serviço final

---

# 🧪 O QUE VOCÊ PROVA COM ESSES TESTES

* ✔ Serviço de diretório
* ✔ Autenticação centralizada
* ✔ LDAP
* ✔ Kerberos (na prática)
* ✔ Samba moderno
* ✔ Diagnóstico

---

# 🧠 COMO EXPLICAR ISSO PARA NÃO TÉCNICOS

Uma frase poderosa:

> “Um domínio completo. Usuários vivem no diretório, autenticam via Kerberos e acessam recursos do Samba, tudo integrado.”

---

# Tutorial: Configuração de Samba AD DC no Ubuntu

Este tutorial guia a configuração de um **Controlador de Domínio Samba AD** no Ubuntu, incluindo criação de usuários, grupos, compartilhamentos e testes de autenticação via Kerberos.

---

## 1. Checar informações do sistema

```
lsb_release -a
hostnamectl
ip a | grep inet
```
---

## 2. Configurar hostname

```
sudo hostnamectl set-hostname dc1
hostname
hostname -f
```

---

## 3. Configurar `/etc/hosts`

Edite o arquivo:

```
sudo nano /etc/hosts
```

Remova a linha existente:

```
127.0.1.1       samba-vnic      samba-vnic
```

Adicione:

```
127.0.0.1       localhost
192.168.56.10   dc1.essias.com.br dc1
```

Teste resolução de hostname:

```
ping -c 2 dc1
ping -c 2 dc1.essias.com.br
```

---

## 4. Instalar pacotes necessários

```
sudo apt update
sudo apt install -y samba krb5-user winbind smbclient dnsutils
```

---

## 5. Parar e desabilitar serviços antigos

```
sudo systemctl stop smbd nmbd winbind
sudo systemctl disable smbd nmbd winbind
```

---

## 6. Backup do `smb.conf` existente

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

---

## 7. Provisionar o domínio Samba AD com RFC2307

```
sudo samba-tool domain provision \
  --realm=ESSIAS.COM.BR \
  --domain=ESSIAS \
  --server-role=dc \
  --dns-backend=SAMBA_INTERNAL \
  --use-rfc2307
```

Verifique se o arquivo foi criado:

```
sudo test -f /etc/samba/smb.conf && echo "smb.conf existe" || echo "smb.conf NÃO existe"
```

---

## 8. Configurar senha do Administrator

```
sudo samba-tool user setpassword Administrator
```

---

## 9. Ativar e iniciar serviço Samba AD DC

```
sudo systemctl enable samba-ad-dc
sudo systemctl start samba-ad-dc
systemctl status samba-ad-dc
```

---

## 10. Listar usuários e testar Kerberos

```
sudo samba-tool user list

kinit Administrator
klist
```

---

## 11. Informações do domínio

```
samba-tool domain info 127.0.0.1
```

---

## 12. Testar registros SRV do DNS interno

```
host -t SRV _ldap._tcp.essias.com.br
```

Se necessário, ajustar DNS:

```
sudo resolvectl dns ens3 127.0.0.1
sudo resolvectl domain ens3 essias.com.br
resolvectl status
```

Para desabilitar systemd-resolved:

```
sudo systemctl disable --now systemd-resolved
sudo rm /etc/resolv.conf
sudo nano /etc/resolv.conf
```

Conteúdo sugerido:

```
search essias.com.br
nameserver 127.0.0.1
```

---

## 13. Criar usuário de teste

```
sudo samba-tool user create usuario.teste
kinit usuario.teste
klist
```

---

## 14. Criar grupo e adicionar usuário

```
sudo samba-tool group create grupo.teste
sudo samba-tool group addmembers grupo.teste usuario.teste
sudo samba-tool group listmembers grupo.teste
```

---

## 15. Criar compartilhamento Samba

Edite `/etc/samba/smb.conf` e adicione:

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

## 16. Preparar diretório compartilhado

```
sudo mkdir -p /srv/samba/teste
sudo chown -R root:20001 /srv/samba/teste
sudo chmod -R 0770 /srv/samba/teste
```

> **Observação:** `20001` é o `gidNumber` do grupo `grupo.teste`.

---

## 17. Reiniciar serviço Samba

```
sudo systemctl restart samba-ad-dc
```

---

## 18. Testar acesso ao compartilhamento

```
smbclient //localhost/Teste -U usuario.teste
```

Comandos dentro do smbclient:

```
ls          # Listar arquivos
mkdir teste # Criar pasta
```

---

## 19. Senha de teste utilizada no tutorial

```
AdmEssias@123
```

---

Pronto! ✅
Com isso, você tem um **Controlador de Domínio Samba AD funcional** com **usuário, grupo, compartilhamento e autenticação Kerberos**.

