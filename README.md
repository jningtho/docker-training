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
