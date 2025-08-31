# TUNNING MONGODB E POSTGRESQL

### sysctl p/ DB pequeno (<5 GB)

O sysctl é a forma de alterar parâmetros do kernel Linux em tempo real (e de forma persistente em /etc/sysctl.d/).
Para bancos de dados, alguns valores default do Linux não são ideais.

```
cat >/etc/sysctl.d/99-db-tuning.conf <<'EOF'
vm.swappiness=10
vm.dirty_ratio=10
vm.dirty_background_ratio=5
fs.file-max=500000
net.core.somaxconn=1024
EOF
sysctl --system
```
### vm.swappiness=10

Controla quanto o kernel tende a usar swap.

Default costuma ser 60 (muito agressivo).

Para DBs, queremos evitar swap (muito lento).

10 = use swap só se realmente estiver sem RAM.

###  vm.dirty_ratio=10

Percentual máximo da RAM que pode ser usado para páginas sujas (dados ainda não gravados no disco).

Se passar de 10%, o kernel força flush pro disco.

Evita que o DB acumule muita escrita em memória e depois sofra um flush gigante.

###  vm.dirty_background_ratio=5

Percentual em que o kernel já começa a escrever páginas sujas em background.

Mantém as gravações mais estáveis, sem bursts.

### fs.file-max=500000

Número máximo de descritores de arquivos (FDs) que o sistema aceita globalmente.

Bancos como PG e Mongo abrem muitas conexões + arquivos de WAL, índices, etc.

Se ficar baixo, pode dar erro “Too many open files”.

### net.core.somaxconn=1024

Número máximo de conexões pendentes na fila de listen().

Ajuda no pico de conexões simultâneas a sockets (útil para bancos de dados).

> Como o banco será pequeno (< 5 GB de dados), não faz sentido exagerar em valores (ex.: shared_buffers=8GB etc). Aqui o objetivo é só melhorar latência e estabilidade.

## Limits (FDs)

Aqui falamos do arquivo /etc/security/limits.conf (ou melhor, limits.d/), que define limites por usuário de quantos arquivos/processos/memória podem ser usados.

Para DBs, se o limite for baixo, eles podem parar de aceitar conexões ou não conseguir abrir arquivos de WAL/índices.

```
cat >/etc/security/limits.d/db-limits.conf <<'EOF'
postgres   soft   nofile  100000
postgres   hard   nofile  100000
mongod     soft   nofile  100000
mongod     hard   nofile  100000
EOF
```

### Usuário postgres (PostgreSQL) e usuário mongod (MongoDB).

nofile = limite de file descriptors (quantos arquivos/conexões podem estar abertos).

soft = limite padrão aplicado no login.

hard = limite máximo que pode ser elevado manualmente (ex.: via ulimit -n).

Por padrão, muitos sistemas deixam nofile em 1024 (muito baixo).
Um banco ativo com centenas/milhares de conexões + arquivos de WAL pode estourar isso.
Por isso, aumentar para algo como 100k é prática comum de hardening.

> Isso garante que PG e Mongo não vão falhar com “Too many open files”.

### Resumindo

sysctl → ajusta parâmetros do kernel para reduzir swap, controlar escrita em disco, aumentar limite global de arquivos, otimizar fila de conexões.

limits (FDs) → aumenta limite por usuário (postgres e mongod), para que possam abrir milhares de conexões/arquivos sem erro.
