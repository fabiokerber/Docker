# Docker

|Training     |Tools|
|-------------|-----------|
|`1.Alura`| Docker

Pré requisito:


Download Docker:<br>
&nbsp;&nbsp;&nbsp;&nbsp;https://www.docker.com/products/docker-desktop

Comandos WSL:<br>
&nbsp;&nbsp;&nbsp;&nbsp;https://docs.microsoft.com/pt-br/windows/wsl/install-manual 

Instalação Ubuntu:<br>
```
$ sudo apt-get remove docker docker-engine docker.io
$ sudo apt-get update
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
$ sudo apt-get update
$ sudo apt-get install docker-ce
$ sudo docker version
$ sudo usermod -aG docker $(whoami)

$ sudo curl -L https://github.com/docker/compose/releases/download/1.15.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

|Tool    |Link|
|-------------|-----------|
|`Docker`| https://desktop.docker.com/win/stable/amd64/Docker%20Desktop%20Installer.exe
|`WSL`| https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi