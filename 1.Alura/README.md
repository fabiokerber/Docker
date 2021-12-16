# 1.Alura

### Docker
<br />

**Anotações**<br>
    *Docker Hub / Docker Store é o repositório oficial de imagens de containers.*<br>
    *Camadas dos containers podem ser "compartilhadas entre si" e as que são baixadas são "read only". Quando altera-se algo é modificado em uma nova camada "read/write".*
<br />

**Início**
```
> docker run hello-world
> docker run ubuntu
> docker ps
> docker ps -a
> docker run ubuntu echo "Ola Mundo"
> docker run -it ubuntu (sobe o container e já conecta no terminal do mesmo)
> docker start <ID>
> docker stop <ID>
```
<br />

**Layered File System (camadas)**
```
> docker rm <ID>
> docker container prune (remove todos os containers inativos/stopped)
> docker images (exibe todas as imagens já baixadas)
> docker rmi hello-world (remove imagem hello-world)
> docker run ubuntu:14.04 (roda container do ubuntu com da versao especifica)
```
<br />

**Praticando**
```
> docker run dockersamples/static-site (imagens não oficiais é necessário informar <mantenedor>/<nome_imagem>)
    > docker ps (outro terminal)
> docker run -d dockersamples/static-site (detached)
> docker container prune
> docker run -d -P dockersamples/static-site (atribui porta externa aleatoria da maquina local para o container)
> docker port <ID> (lista portas em uso pelo container)
    http://localhost:<port>
> docker run -d -P --name meu-site dockersamples/static-site (atribui o nome "meu-site" ao container)
> docker stop -t 0 meu-site (interrompe o container de forma mais rápida)
> docker run -d -p 12345:80 --name meu-site dockersamples/static-site (mapeia porta 12345 local para a porta 80 do container)
> docker run -d -P -e AUTHOR="Borracha" --name meu-site dockersamples/static-site (starta o container com um valor atribuído a variável AUTHOR)
    > http://localhost:<port>
> docker ps -q (lista somente os ID's dos containers)
> docker stop $(docker ps -q) (para todos os containers listados com o ps -q)
```
<br />

**Salvando dados com volumes**
```
> docker run -v "/var/www" ubuntu (mapeia a pasta /var/lib... para /var/www dentro do container)
> docker inspect <ID>
    Mounts...
> docker run -it -v "C:\Temp:/var/www" ubuntu (mapeia a pasta C:\Temp para /var/www dentro do container)
docker run -p 8080:3000 -v "C:\Temp:/var/www" -w "/var/www" node npm start ("inicia" o container na pasta /var/www e executa o comando "node npm start", logo apos a criação do container)
> docker run -p 8080:3000 -v "$(pwd):/var/www" -w "/var/www" node npm start
```
<br />

**Criando um Dockerfile e "buildando"**
```
Criar 01.dockerfile
---
FROM node:latest (monta imagem a partir de uma outra imagem fonte)
MAINTAINER Fabio Kerber (mantenedor da imagem, quem é responsável pela imagem - depreciado por LABEL)
COPY . /var/www (copia conteudo pasta local para /var/www)
RUN npm install (executa comando apos a criação do container)
WORKDIR /var/www (seta o path padrao para execucao dos comandos abaixo - no exemplo os arquivos estao em /var/www)
ENTRYPOINT [ "npm", "start" ](quando imagem for startada tera um comando de entrada - funciona conforme acima também)
EXPOSE 3000 (permite a exposição da porta 3000)
---

> docker build -f 01.dockerfile -t fabiokerber/node 01.dockerfile (-f indicar arquivo a ser buildado | -t <mantenedor>/<nomeimagem>)

> docker build -f lab.dockerfile -t meu_ubuntu .
> docker images
```
<br />

**Networking**
```

```
<br />