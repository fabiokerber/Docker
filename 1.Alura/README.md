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