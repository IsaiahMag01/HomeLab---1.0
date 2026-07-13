# 06 Mounting Pool
## Why:
- You are gonna want more storage so you have somewhere to put the files for your beutiful new media container

## Setup:
1. Go to the new container
2. Resources
3. Add
4. Mount
5. Mount Point ID: 0 is ok
6. Select where you are pulling storage from
7. Disk size - 1000GiB
8. Set your Path:
  - This is where your docker and applications will point to so you wanna make sure you set it up right from the jump
  - ```/data```
9. Not Backing Up Here
10. Will now have 1000 GiB free

## Setup Mount point for docker...
1. Container
2. Resources
3. Add
4. Mount
5. Mount point ID: 1
6. Storage: local-lvm
7. Disk Size: 32Gib
8. Path: /docker
9. No backup

## Trust but Verify:
1. Turn on your container
2. Console
3. Login:
  - Root
  - Password
4. Update your system!
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```
5. ls into root
  - Wanna be able to seee /data and /docker
