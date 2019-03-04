## Work in progress
### Stack tested using docker-machine version 0.16.1, build cce350d7, using Virtualbox provider.

Brings up dockers machine for the following CI components in the mentioned ports: 
* portainer: 8080
* jenkins: 8081
* gogs: 8082
* nexus: 8083
* sonarqube: 8084

```docker-machine create -d virtualbox --virtualbox-disk-size "50000" <machine-name>```
```docker-machine create -d generic --generic-ssh-user vagrant --generic-ssh-key ~/.vagrant.d/insecure_private_key --generic-ip-address <ip-address> <machine-name>```
To fix 0.0.0.0 published address/ports in Portainer:
```docker-machine ssh <machine-name>
vi /etc/init.d/docker
dockerd --data-root "$DOCKER_DIR" -H unix:// --ip=192.168.99.102 $EXTRA_ARGS --pidfile "$PIDFILE" >> /var/lib/boot2docker/log/docker.log 2>&1 &
sudo /etc/init.d/docker restart```
