## Intro

This docker-compose setup allows you to easily spin up a security testing/research environment.

The main purpose is to create a separate network and containers that can be referenced by name.

This also allows you to have multiple containers listening on the same port to avoid confusing port mappings.

This repo started based on both Vulhub and SecurityWeekly's repos on building a docker lab.

I've modified this to fit my own needs.


## Prerequisites

You must have Docker installed to your system.

Linux:
..
1. sudo apt install -y docker.io

2. sudo systemctl enable docker --now

3. sudo usermod -aG docker $USER
..


## Usage

Simply clone this repository and run:

``
docker-compose up -d
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

Modify for your own needs!

Thanks to Vulhub: https://github.com/vulhub/vulhub
Thanks to SecurityWeekly: https://github.com/SecurityWeekly/vulhub-lab
