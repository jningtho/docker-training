# Docker Training module


## 1. Docker Setup and Configuration
- Docker for [MAC](https://docs.docker.com/docker-for-mac/install/)
- Docker for [Windows](https://docs.docker.com/docker-for-windows/install/)
- Docker for [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)
- Docker for [Centos](https://docs.docker.com/install/linux/docker-ce/centos/)
- Docker CE on Ubuntu

## Prerequisites
### OS requirements
To install Docker CE, you need the 64-bit version of one of these Ubuntu versions:

- Artful 17.10 (Docker CE 17.11 Edge and higher only)
- Xenial 16.04 (LTS)
- Trusty 14.04 (LTS)

## Installation Details
[Ubuntu 16.04](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

### Install using the repository
Before you install Docker CE for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

### Setup the repository

1. Update the apt package index:
```
$ sudo apt-get update
```
2. Install packages to allow apt to use a repository over HTTPS:
```
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```
3. Add Docker’s official GPG key:
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Verify that you now have the key with the fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88, by searching for the last 8 characters of the fingerprint.

```
$ sudo apt-key fingerprint 0EBFCD88

pub   4096R/0EBFCD88 2017-02-22
      Key fingerprint = 9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid                  Docker Release (CE deb) <docker@docker.com>
sub   4096R/F273FCD8 2017-02-22

```
4. Use the following command to set up the stable repository. You always need the stable repository, even if you want to install builds from the edge or test repositories as well. To add the edge or test repository, add the word edge or test (or both) after the word stable in the commands below.

```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
### INSTALL DOCKER CE

1. Update the apt package index.
```
$ sudo apt-get update
```

2. Install the latest version of Docker CE, or go to the next step to install a specific version. Any existing installation of Docker is replaced.
```
$ sudo apt-get install docker-ce
```
3. Verify that Docker CE is installed correctly by running the hello-world image.
```
$ sudo docker run hello-world
```

This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.

Docker CE is installed and running. The docker group is created but no users are added to it. You need to use sudo to run Docker commands. Continue to [Post-installation steps for Linux](https://docs.docker.com/install/linux/linux-postinstall/) to allow non-privileged users to run Docker commands and for other optional configuration steps.

## Post-installation steps for Linux

### Manage Docker as a non-root user

The docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the user root and other users can only access it using sudo. The docker daemon always runs as the root user.

If you don’t want to use sudo when you use the docker command, create a Unix group called docker and add users to it. When the docker daemon starts, it makes the ownership of the Unix socket read/writable by the docker group.

To create the docker group and add your user:

1. Create the docker group.
```
$ sudo groupadd docker
```
2. Add your user to the docker group.
```
$ sudo usermod -aG docker $USER
```
3. Log out and log back in so that your group membership is re-evaluated.

        If testing on a virtual machine, it may be necessary to restart the virtual machine for changes to take effect. On a desktop Linux environment such as X Windows, log out of your session completely and then log back in.

4. Verify that you can run docker commands without sudo
```
$ docker run hello-world
```
This command downloads a test image and runs it in a container. When the container runs, it prints an informational message and exits.

If you initially ran Docker CLI commands using sudo before adding your user to the docker group, you may see the following error, which indicates that your ~/.docker/ directory was created with incorrect permissions due to the sudo commands.

WARNING!
```
WARNING: Error loading config file: /home/user/.docker/config.json -
stat /home/user/.docker/config.json: permission denied
```
To fix this problem, either remove the ~/.docker/ directory (it is recreated automatically, but any custom settings are lost), or change its ownership and permissions using the following commands:

```
$ sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
$ sudo chmod g+rwx "/home/$USER/.docker" -R
```
