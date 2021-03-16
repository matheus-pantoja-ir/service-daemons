[:back: voltar](/README.md)

# Ubuntu (upstart)
1. Criar um usuário e o grupo para o serviço
```bash
sudo useradd service_name
sudo groupadd service_group_name
sudo usermod -aG service_group_name service_name 
```
> para conferir se deu certo `grep service_group_name /etc/group`


2. Ajustar as variaveis do arquivo `debian`
```
env APPUSER="service_name"
env APPDIR="/usr/bin"
env APPBIN="node"
env APPARGS="server.js"
``` 

3. renomear o arquivo `ubuntu` para `my_service` e mover para pasta `/etc/init.d`
```bash
sudo mv ubuntu /etc/init/my_service.conf
```

4. iniciar o serviço
``` bash
sudo start my_service
```