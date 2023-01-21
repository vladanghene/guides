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
OR even simpler:

If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group:

```console
sudo usermod -aG docker ${USER}
``` 
To apply the new group membership, log out of the server and back in, or type the following:
```console
su - ${USER}
```
You will be prompted to enter your user’s password to continue.

Confirm that your user is now added to the docker group by typing:
```console
groups
```
Output
```console
seinfeld sudo docker
```
If you need to add a user to the docker group that you’re not logged in as, declare that username explicitly using:
```console
sudo usermod -aG docker username
```
The rest of this article assumes you are running the docker command as a user in the docker group. If you choose not to, please prepend the commands with sudo.

From this digitalocean [guide on docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04).

---
##### Installing docker-compose latest official stable version

First, go check their [github](https://github.com/docker/compose) and on the right side you'll see Latest "v2.15.1" (at the time of this commit).
Then declare a var in your bash:
```console
dcver=
```
Then simply run this curl to get it:
```console
sudo curl -L "https://github.com/docker/compose/releases/download/${dcver}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
And last but not least, make it executable:
```console
sudo chmod +x /usr/local/bin/docker-compose
```
Now you can check if it's running smoothly:
```console
docker-compose --version
```

Fron this digitalocean [guide on installing docker-compose](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04)


