### 📁 **Arquivos e diretórios**

```bash
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

### 🌐 **Rede**

```bash
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

# Ver rota
traceroute google.com

# Baixar arquivos via rede
wget http://site.com/arquivo.txt
curl -O http://site.com/arquivo.txt
```

---

### 🛠️ **Serviços (systemd)**

```bash
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

### 🧠 **Uso de sistema (CPU, memória, disco)**

```bash
top                  # Ver uso de CPU e memória em tempo real
htop                 # Melhorado (instale com apt install htop)
free -h              # Uso de memória
df -h                # Espaço em disco
du -sh *             # Espaço por pasta

# Ver processos com uso de porta, CPU, etc.
ps aux | grep nome
```

---

### 🔧 **Manutenção e diagnóstico**

```bash
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

### 🔄 **JSON & Webservices**

```bash
# Formatar e ler JSON
jq . arquivo.json

# Buscar dados de API REST
curl -X GET http://api.site.com/endpoint
curl -X POST -H "Content-Type: application/json" \
     -d '{"chave":"valor"}' http://api.site.com/endpoint
```

---

### 💡 Extras úteis

```bash
# Ver variável de ambiente
echo $VARIAVEL

# Exportar variável
export VARIAVEL=valor

# Ver todos os IPs conectados (útil para dispositivos de rede)
arp -a

# Buscar nome de host
hostname
hostname -I        # Só o IP
```

---

Se quiser, posso gerar esse conteúdo em um arquivo `.sh`, `.txt` ou `.md` para você levar em pendrive, GitHub ou manter como documentação interna. Deseja isso? Posso incluir observações ou exemplos práticos baseados nas manutenções que você mais faz também.
