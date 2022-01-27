## Intro

This docker-compose setup allows you to easily spin up a security testing/research environment.

The main purpose is to create a separate network and containers that can be referenced by name.

This also allows you to have multiple containers listening on the same port to avoid confusing port mappings.

Modify for your own needs!


## Credits

-Original Idea (Vulhub): https://github.com/vulhub/vulhub

-Modified Code (SecurityWeekly): https://github.com/SecurityWeekly/vulhub-lab


## Prerequisites

You must have Docker installed to your system.

Linux:
```
1. sudo apt install -y docker.io --fix-missing

2. sudo systemctl enable docker --now

3. sudo usermod -aG docker $USER

4. sudo apt install docker-compose

```


## Usage

Simply clone this repository and run:

``
sudo docker-compose up -d
``

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

```

To interact with Kali directly from the command line:
```
sudo docker exec -it kali /bin/bash
```


## Shutdown Containers
When you are done and ready to shutdown:
```
sudo docker-compose down -v
```

## Rebuild Containers
If you need to rebuild a container from scratch (rebuild Kali example):
```
sudo docker-compose build --no-cache service_name

sudo docker-compose build --no-cache kali
```


## Remove Containers
If you want to completely remove the containers:
```
1. sudo docker-compose stop

2. sudo docker-compose rm
```
