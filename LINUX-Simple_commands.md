### **Arquivos e diretórios**

```
# Ler arquivo texto ou JSON
cat /caminho/arquivo.txt
less /caminho/arquivo.json
jq . /caminho/arquivo.json    # Leitura JSON formatada (precisa do jq)

# Ver últimas linhas (logs, por exemplo)
tail -n 50 /var/log/syslog
tail -f /var/log/syslog       # "Seguir" o log ao vivo

# Buscar conteúdo em arquivos
grep "palavra" /caminho/arquivo.txt
grep -r "palavra" /caminho/da/pasta/

# Copiar, mover, remover
cp origem destino
mv origem destino
rm -rf /caminho               # CUIDADO com o -rf
```
---

### **Updates**

```
# Pos-instalação.
sudo dnf clean all        # limpa cache de pacotes antigos
sudo dnf -y update        # aplica todas as atualizações
sudo reboot               # reinicia para carregar kernel/patches
```


---

### **Rede**

```
bash
# Ver IP e interfaces
ip a
ifconfig         # Pode precisar instalar: apt install net-tools

# Testar conexão
ping 8.8.8.8
ping google.com

# Testar porta aberta
nc -zv ip_ou_host 80

# Ver conexões abertas e escutando
ss -tulnp
netstat -tulnp        # Também com net-tools

# Testar DNS
dig google.com
nslookup google.com

# Limpar cache DNS
sudo systemd-resolve --flush-caches

# Desabilitar IPV6
# Adicione as linhas abaixo no arquivo /etc/sysctl.conf depois aplique usando o comando sudo sysctl -p:
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1

sudo sysctl -p

# Renomear uma interface
sudo ip link set dev eth0 name neweth0

# Ver rota
traceroute google.com

# Habilitar ou desabilitar que o NetworkManager escreva o /etc/resolv.conf
sudo chattr -i /etc/resolv.conf
sudo chattr +i /etc/resolv.conf

# Baixar arquivos via rede
wget http://site.com/arquivo.txt
curl -O http://site.com/arquivo.txt
```

---

### **Serviços (systemd)**

```
# Ver status do serviço
systemctl status nome_do_serviço

# Iniciar, parar, reiniciar
systemctl start nome_do_serviço
systemctl stop nome_do_serviço
systemctl restart nome_do_serviço

# Habilitar ao iniciar o sistema
systemctl enable nome_do_serviço
systemctl disable nome_do_serviço

# Ver serviços em execução
systemctl list-units --type=service --state=running
```

---

### **Uso de sistema (CPU, memória, disco)**

```
top                  # Ver uso de CPU e memória em tempo real
htop                 # Melhorado (instale com apt install htop)
free -h              # Uso de memória
df -h                # Espaço em disco
du -sh *             # Espaço por pasta

# Ver processos com uso de porta, CPU, etc.
ps aux | grep nome
```

---

### **Manutenção e diagnóstico**

```
# Ver dmesg (mensagens de kernel)
dmesg | tail -n 20

# Ver logs do sistema
journalctl -xe         # Logs recentes com erros
journalctl -u nome_do_serviço

# Ver drivers e dispositivos conectados
lsusb                  # USB (câmeras OCR, leitores RFID)
lspci                  # Dispositivos PCI
dmesg | grep tty       # Dispositivos seriais

# Ver permissões de arquivos
ls -l /caminho

# Testar leitura serial (se necessário)
screen /dev/ttyUSB0 9600
```

---

### **JSON & Webservices**

```
# Formatar e ler JSON
jq . arquivo.json

# Buscar dados de API REST
curl -X GET http://api.site.com/endpoint
curl -X POST -H "Content-Type: application/json" \
     -d '{"chave":"valor"}' http://api.site.com/endpoint
```

---

### **Extras úteis**

```
# Ver variável de ambiente
echo $VARIAVEL

# Exportar variável
export VARIAVEL=valor

# Ver todos os IPs conectados (útil para dispositivos de rede)
arp -a

# Buscar nome de host
hostname
hostname -I        # Só o IP

# Rodar script ou comando em segundo plano
sudo nohup /script/path.sh > /path/to/save/log$(date +%Y%m).log 2>&1 & disown

# Rodar find e salvar resultado em segundo plano.
nohup find /caminho/para/buscar/ -type f -name 'PARTE_DO_NOME_DO_ARQUIVO*' > ENCONTRADOS.TXT 2>/dev/null &
```
## SED COMMAND
---

### 1. **Basic example: Delete lines containing "ERROR". It doesn't save the file**

```
sed '/ERROR/d' file.txt
```

* This prints the contents of `file.txt`, **excluding** any line that contains `ERROR`.

### 2. **Edit the file in-place (overwrite original)**

```
sed -i '/ERROR/d' file.txt
```

* This removes all lines containing `ERROR` **and saves the result back** to `file.txt`.

### 3. **Case-insensitive match**

```
sed -i '/error/Id' file.txt
```

* `I` makes it **case-insensitive**. Will remove lines with `Error`, `ERROR`, `error`, etc.

### 4. **Delete lines containing multiple terms (e.g., ERROR or WARNING)**

```
sed -i '/ERROR\|WARNING/d' file.txt
```

* Removes any line that contains `ERROR` **or** `WARNING`.

### 5. **Delete lines that match a pattern like an IP address**

```
sed -i '/[0-9]\{1,3\}\(\.[0-9]\{1,3\}\)\{3\}/d' file.txt
```

* Removes lines with something that **looks like an IPv4 address**.

### 6. **Remove lines containing the word only as a full word**

```
sed -i '/\<ERROR\>/d' file.txt
```

* `\<` and `\>` make sure it only removes lines with the **whole word** `ERROR`, not words like `ERROR123`.

### 7. **Remove lines starting with a specific word (e.g., comments)**

```
sed -i '/^#/d' file.txt
```

* Deletes lines that **start with a hash** `#`, commonly used in config files.
