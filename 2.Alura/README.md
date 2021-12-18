# 2.Alura

### Docker Swarm (ORQUESTRADOR) & Docker Machine
<br />

**Anotações**<br>
    *Docker machine cria máquinas virtuais com o auxilio do VirtualBox já com o docker instalado.*
<br />

**Docker Machine**
*Git BASH*
```
$ docker-machine rm vm{0,1,2,3,4,5}
$ docker-machine create -d virtualbox vm1 (se erro reinstalar o VirtualBox)
```
<br />

**Criando cluster de VMs**
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

**Criando workers**
*Git BASH*
```
$ docker-machine create -d virtualbox vm2
$ docker-machine create -d virtualbox vm3

!! Acessar vm2 e vm3 e adicioná-las com o token ao cluster swarm !!
```
<br />

**Listando e removendo nós (worker)**
*Git BASH*
```
$ docker-machine ssh vm3
  $ docker swarm leave

$ docker-machine ssh vm1
  $ docker node ls (lista managers e workers do swarm)
  $ docker node rm <ID_NODE_vm3>
```
<br />