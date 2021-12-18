# 2.Alura

### Docker Swarm (ORQUESTRADOR) & Docker Machine
<br />

**Anotações**<br>
    *Docker machine cria máquinas virtuais com o auxilio do VirtualBox já com o docker instalado.*
<br />

**Docker Machine**<br>
*Git BASH*
```
$ docker-machine rm vm{0,1,2,3,4,5}
$ docker-machine create -d virtualbox vm1 (se erro reinstalar o VirtualBox)
```
<br />

**Criando cluster de VMs**<br>
*Git BASH*
```
$ docker-machine ssh vm1
  $ docker swarm init --advertise-addr 192.168.99.101 
  (inicia o swarm com o IP atribuido à esta maquina virtual)
  (esta maquina também se tornou o 'manager' deste swarm)
$ docker inspect vm1
  Role: manager
$ docker swarm join-token worker (exibe o comando para adicionar workers)
```
<br />

**Criando workers**<br>
*Git BASH*
```
$ docker-machine create -d virtualbox vm2
$ docker-machine create -d virtualbox vm3

!! Acessar vm2 e vm3 e adicioná-las com o token ao cluster swarm !!
```
<br />

**Listando e removendo nós (worker)**<br>
*Git BASH*
```
$ docker-machine ssh vm3
  $ docker swarm leave

$ docker-machine ssh vm1
  $ docker node ls (lista managers e workers do swarm)
  $ docker node rm <ID_NODE_vm3>
```
<br />

**Subindo serviço e Routing Mesh**<br>
*Git BASH*
```
$ docker-machine start vm{1,2,3}
$ docker-machine ssh vm2
  $ docker container run -p 8080:3000 -d aluracursos/barbearia
  $ docker container ls

$ docker-machine ssh vm1
  $ docker inspect vm2 (pegar informações sobre o vm2)
  $ docker service create -p 8080:3000 -d aluracursos/barbearia (ira criar um container mas como serviço no swarm)
  $ docker service ls (exibe o status e replicação do serviço)
  $ docker service ps <ID _service>
  http://ip_vm{1,2,3}:8080 (routing mesh redireciona indenpente de onde o container estiver funcionando)
```
<br />

**Subindo serviço e Routing Mesh**<br>
*Git BASH*
```
$ docker-machine start vm{1,2,3}
$ docker-machine ssh vm2
  $ docker container run -p 8080:3000 -d aluracursos/barbearia
  $ docker container ls

$ docker-machine ssh vm1
  $ docker inspect vm2 (pegar informações sobre o vm2)
  $ docker service create -p 8080:3000 -d aluracursos/barbearia (ira criar um container mas como serviço no swarm)
  $ docker service ls (exibe o status e replicação do serviço)
  $ docker service ps <ID _service>
  http://ip_vm{1,2,3}:8080 (routing mesh redireciona indenpente de onde o container estiver funcionando)
```
<br />

**Backup do Swarm**<br>
*Git BASH*
```
$ docker-machine ssh vm1
  $ sudo su
  $ ls /var/lib/docker/swarm
  $ cp -r /var/lib/docker/swarm backup (faz o backup da pasta swarm que contem todas as configurações e logs do swarm)
  (caso ocorra algum problema com o manager, basta copiar esse conteudo para a pasta swarm novamente)
  (apos a copia, basta subir o swarm novamente adicionando a flag --force-new-cluster)
```
<br />