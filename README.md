## Intro

This docker-compose setup allows you to easily spin up a security testing/research environment.

The main purpose of this environment is to create a dedicated network with containers that can be referenced by their hostname.

This also allows you to have multiple containers listening on the same port to avoid conflicting port mappings.

Add, delete or update the list of vulnerable containers for your own needs!

## Credits

- Original Idea (Vulhub): https://github.com/vulhub/vulhub
- Modified Code (SecurityWeekly): https://github.com/SecurityWeekly/vulhub-lab

## Prerequisites

You must have Docker installed on your system. Below are the instructions for installing Docker on Linux.

```
sudo apt install -y docker.io --fix-missing
sudo systemctl enable docker --now
sudo usermod -aG docker $USER
sudo apt install docker-compose
```

## Usage

To start the lab, clone this repository and run the command

```
docker-compose up
```

Important points about this command:
- The `docker-compose` command first builds the images and then starts the containers. If the images are not yet present on the docker host, building them might take a while.
- The `docker-compose.yml` file at the root level specifies the containers to be deployed. If you want just a few of the containers for testing purposes, feel free to comment out the containers in this file you don't need.
- If the any of the commands in this repo fail, you might need to use `sudo <command>` to run as root.

To list the running containers (and their IP addresses) run

```
docker ps
```

To interact with your Kali Linux container for testing run

```
docker exec -it kali /bin/bash
```

Since we are starting a bash shell in the Kali container, you should see the default Kali prompt and have autocompletion enabled.

Once you are done with the lab, run 

```shell
docker-compose down
```

to stop and remove the running containers.
