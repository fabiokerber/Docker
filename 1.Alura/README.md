# 1.Alura

### Docker
<br />

**Anotações**<br>
    *Docker Hub / Docker Store é o repositório oficial de imagens de containers.*
    *Camadas dos containers podem ser "compartilhadas entre si" e as que são baixadas são "read only". Quando altera-se algo é alterado em uma nova camada "read/write".*
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

**Layered File System**
```
> docker rm <ID>
> docker container prune (remove todos os containers inativos/stopped)
> docker images (exibe todas as imagens já baixadas)
> docker rmi hello-world (remove imagem hello-world)
> docker run ubuntu:14.04 (roda container do ubuntu com da versao especifica)
```
<br />