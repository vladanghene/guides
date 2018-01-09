#### After you use dnf to install docker, here's a neat way to simply never need sudo for docker again.

###### First off make sure your service manager is configured to account for Docker (I use Fedora so mine is systemctl)

```
sudo systemctl enable docker
```
###### Now for the privileges

Simply add a docker group, add yourself to it and restart docker service. Then you need to log off and back on for privileges to flush, or simply use the newgrp cmd as below. Commands were provided by [FedoraProject](https://developer.fedoraproject.org/tools/docker/docker-installation.html)

###### Run Docker commands without sudo
```console
$ sudo groupadd docker && sudo gpasswd -a ${USER} docker && sudo systemctl restart docker
$ newgrp docker
```
