# Conteineirização com DOCKER.

## Imagens de containeres do DOCKER HUB.

O Docker Hub é uma plataforma de armazenamento de imagens de containers Docker onde podemos pesquisar as imagens que queremos. Cada inmagem carrga em sua página as instruções e informações sobre a imagem.

Para fazer o download da imagem basta digitar no terminal

`docker pull <nome-da-imagem>`


Quando executado o comando `docker pull <nome-da-imagem>` sem definir a TAG o docker vai baixar a versão `latest`.


## Comandos uteis do docker 

Para ver as imagens baixadas no seu ambiente execute o comando

`docker images`


Para executar ama imagem digite o comando:

`docker run <nome-da-imagem>`

`docker container run <nome-da-imagem>` (nova sintaxe)


Para exeuctar o container por um tempo execute o comando abaixo:

`doker run <nome-da-imagem> sleep XX` (XX = segundos)


Para parar um container basta usar o comando abaixo usando o nome do container ou o ID.

`docker stop <nome-ou-ID-do-container>`


Para iniciar um container basta usar o comando abaixo usando o nome do container ou o ID.

`docker start <nome-ou-ID-do-container>`


Para rodar um container com o terminal tty (-t) interativo (--internative). Ao sair do terminal o conteiner é finalizado.

`docker run -it <nome-da-imagem>`


Para ver os containeres em execução digite o comando:

`docker ps`

`docker container ls` (nova sintaxe)


Para ver todos os containeres inclusive os que não estão em execução, mas foram executados recentemente.

`docker ps -a`


## Executando aplicações no container

Executando o container em backgroud que estará sempre em execução.

`docker run -d <nome-da-imagem>`


Abrir o terminal executando alguma aplicação. Neste caso o bash para ter o terminal. (Ao sair do terminal, sai do container, mas continua em execução)

`docker exec -it <os-3-primeiros-digitos-do-ID-do-container> /bin/bash` 


Rodando um comando dentro do container e saindo do container. Exemplo.

`docker exec -it <os-3-primeiros-digitos-do-ID-do-container> cat /etc/hosts`

`docker exec -it <os-3-primeiros-digitos-do-ID-do-container> ip a`

## Rename no container (Delete container e imagens)

Renomeando o container:

`docker run -dti --name <nome-do-container> <nome-da-imgem>`


Removendo container

`docker rm <os-3-primeiros-digitos-do-ID-do-container>`


Deletando imagem:

`docker rmi <nome-da-imagem>`


## Troca de arquivos com o container

Enviando arquivos da máquina local para o container.

`docker cp /caminho/do/arquivo <nome-da-maquina>:/pasta/de/destino`


Copiando arquivo do container para a máquina local:

`docker cp <nome-da-maquina>:/pasta/de/origem/arquivo.extensao> /caminho/de/destino-local/`


## TAGS

As TAG são usadas para indicar a versão 

`docker pull <nome-da-imagem>:<tag>`

`docker pull debian:9` baixando a versão 9 da imagem do Debian


## Criando um container com aplicação específica

Alguns containers para rodar precisam de alguns parâmetros configurados no momento da inicialização e devem ser declarados no terminal. No exemplo a seguir vamos rodar um container mysql informando também as variáveis de ambiente conforme está na página do container no Dock Hub.

`docker run -e MYSQL_ROOT_PASSWORD=<senha> --name <nome-do-container> -d -p 3306:3306 mysql`

- docker run (para rodar)
- -e para indicar que há uma váriável de ambiente. Neste exemplo MYSQL_ROOT_PASSWORD.
- --name para dar o nome ao container.
- -d para rodar em segundo plano
- -p para indicar a porta que o container será exposto.
- mysql (nome da imagem)


## Verificar informações sobre um container.

Para ver as informações sobre o container:

`docker inspect <nome-do-container>`


# ARMAZENAMENTO DE DADOS EM CONTAINER

# PROCESSAMENTO, LOGS E REDE COM DOCKER

# DEFINIÇÃO E CRIAÇÃO DE UM DOCKER FILE

# TRABALHANDO COM DOCKER COMPOSE

