[:back: voltar](/README.md)

# Debian/Ubuntu (sysvinit)
1. Criar um usuário e o grupo para o serviço
```bash
sudo useradd service_name
sudo groupadd service_group_name
sudo usermod -aG service_group_name service_name 
```
> para conferir se deu certo `grep service_group_name /etc/group`

2. Ajustar as variaveis do arquivo `debian`
```
NAME="my_service"
PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
APPDIR="/path/to/main/archive"
APPBIN="/path/to/application/bin"
APPARGS="application -arg value"
USER="service_name"
GROUP="myservice_group"
``` 

3. renomear o arquivo `debian` para `my_service` e mover para pasta `/etc/init.d`
```bash
sudo mv debian /etc/init.d/my_service
```

4. Dar a permissão de executavel para o arquivo
``` bash
sudo chmod +x /etc/init.d/my_service
```

5. Atualizar o deamon 
```bash
update-rc.d my_service defaults
```

6. iniciar o serviço
```bash 
service my_service start
# conferir se esta tudo certo
service my_service status
```
