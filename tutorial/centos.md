[:back: voltar](/README.md)
# CentOS
1. Criar um usuário e o grupo para o serviço
```bash
sudo useradd service_name
sudo groupadd service_group_name
sudo usermod -aG service_group_name service_name 
```
> para conferir se deu certo `grep service_group_name /etc/group`

2. Ajustar as variaveis do arquivo `centos`
```
USER="service_name"
APPNAME="my_service"
APPBIN="/path/to/application/bin"
APPARGS="application -arg value"
LOGFILE="/var/log/$APPNAME/error.log"
LOCKFILE="/var/lock/subsys/$APPNAME"
``` 

3. renomear o arquivo `centos` para `my_service` e mover para pasta `/etc/init.d`
```bash
sudo mv centos /etc/init.d/my_service
```

3. Dar a permissão de executavel para o arquivo
``` bash
sudo chmod +x /etc/init.d/my_service
```

4. Atualizar o deamon 
```bash
chkconfig my_service on
```

5. iniciar o serviço
```bash 
service my_service start
# conferir se esta tudo certo
service my_service status
```


