Installing docker
====


Preconditions
----
* OS: Ubuntu 14.04 trusty


Installation
----
```bash
$ sudo apt-get update
$ sudo apt-get install apt-transport-https ca-certificates
$ sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D # Adding GPG key
$ echo "deb https://apt.dockerproject.org/repo ubuntu-trusty main" > /etc/apt/sources.list.d/docker.list # Update APT sources list
$ sudo apt-get update # Update APT cache
$ sudo apt-get purge lxc-docker # Remove old repo (if any)
$ sudo apt-get install linux-image-extra-$(uname -r) # Install kernel package
$ sudo apt-get install docker-engine # Install docker
```


Starting docker daemon
----
```bash
sudo service docker start
```


Resources
----
[Docker installation doc](https://docs.docker.com/engine/installation/linux/ubuntulinux/)
