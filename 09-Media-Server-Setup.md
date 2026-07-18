# Media Server Setup
## What has been done:
1. Proxmox has been setup fully (Migrated over to my Dell Vostro)
2. Removed the enterprise subscriptions
3. Added the non-enterprise subscriptions
4. Confirmed the maximum mount of space on my local-lvm partition so I can maximize the amount of containers and configurations one each container independent of my external drive and NAS 
5. Updated Proxmox
6. ZFS Pool has been created - Bulk storage from one of the 2TB internal drives that I installed from another rig
7. Created an Ubuntu Server Container
  - 8GB Memory
  - 4 Cores
  - Root disk - 80GB
8. Mounted two partitions to my ubuntu container:
  - 1000GB - From Bulk Storage - /docker
  - 30GB - From local-lvm for - /docker
9. Updated container
10. Created local user - isaiah
    - Made it the owner of the data and docker container so I can continue to work on the workstation without being in root
    - Has sudo
11. Congiured samba share + user to access it
  - Installed tools to ensure worked on windows
12. Confirm works fully on my windows desktop

## What Doing Here:
- Configuring this ubuntu server to act as the source of my media server - R-Suit + Plex stored within a docker container

## Docker Setup:
- Went to the [Docker Github Page](https://github.com/docker) -> [Docker Install Guide](https://github.com/docker/docker-install)
- Installed from Get-Docker.com
```bash

curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh

```
- Ran into some issues so I used some lovely modern tools to help me understand what was going on as no matter how many times ran this I could not get the test to work

### Assistant from new tool:
1. Updated my system
2. Installed Make Tool kit to assist in future projects:
```bash
sudo apt install build-essential
```
3. Followed the instructions again:
```bash

curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

```
4. Tested docker was running cleanly:
```bash

sudo docker run hello-world
```

- Result:
```bash

Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

# Now I wanna run Docker without using sudo every time
- Resource: [TechHut - Managing Docker as a non-root user](https://techhut.tv/7-docker-basics-for-beginners)
## What I am doing here:
- To avoid having to use sudo every time I am working with docker I am adding my user on this server to the docker group - ***NOTE: This does give high-level privilages so have to be careful once I begin using it***
Commands:
```bash
sudo usermod -aG docker $USER
newgrp docker
```



