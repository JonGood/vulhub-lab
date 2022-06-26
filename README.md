## Intro

This docker-compose setup allows you to easily spin up a security testing/research environment.

The main purpose of this environment is to create a dedicated network with containers that can be referenced by name.

This also allows you to have multiple containers listening on the same port to avoid conflicting port mappings.

Add/delete/update the containers for your own needs!

## Credits

- Original Idea (Vulhub): https://github.com/vulhub/vulhub
- Modified Code (SecurityWeekly): https://github.com/SecurityWeekly/vulhub-lab

## Prerequisites

You must have Docker installed on your system. Below are the instructions to install Docker on Linux.

```
sudo apt install -y docker.io --fix-missing
sudo systemctl enable docker --now
sudo usermod -aG docker $USER
sudo apt install docker-compose
```

## Usage

Clone this repository and run the command

```
docker-compose up -d
```

Be certain to add the following to your /etc/hosts file:

```
# Vulhub lab
10.1.1.5        shellshock
10.1.1.6        jenkins
10.1.1.7        phpmyadmin
10.1.1.8        mysql
10.1.1.9        telnetserver
10.1.1.10       kali
10.1.1.11       solr-log4j
10.1.1.12       tomcat
```

List docker containers AND ports:
```
docker ps
```

To interact with Kali directly from the command line:

```
docker exec -it kali /bin/bash
```

## Shutdown Containers
When you are done and ready to shutdown:

```
docker-compose down -v
```

## Rebuild Containers
If you need to rebuild a container from scratch (rebuild Kali example):

```
docker-compose build --no-cache [service_name]
docker-compose build --no-cache kali
```

## Remove Containers
If you want to completely remove the containers:
```
sudo docker-compose stop
sudo docker-compose rm
```
