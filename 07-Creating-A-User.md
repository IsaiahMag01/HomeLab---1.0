# 07 Creating a user
## Why:
- You do not wanna operate out of root 100 percent of the time - that can have some consequences

## Proccess:
1. adduser <name>
2. set password - put in your password manager!
3. Set any of the info you want... you are the only one on this system so it does not matter much!

## Add to the sudo group so can use sudo
```bash
adduser <name> sudo
```
## Switching to your user:
```bash
su <username>
```

## Change some permissions:
- If you go to interact with these files you will get a perm denied... need to make user owner of both directories
1. Set Perms
```bash
sudo chown -R youruser:youruser /data
sudo chown -R youruser:youruser /docker
```
2. Ran into a snag:
```bash
isaiah@media:/$ sudo chown -R isaiah:isaiah /docker

chown: cannot read directory '/docker/lost+found': Permission denied

isaiah@media:/$ ls

bin   data  docker  home  lib32  libx32      media  opt   root  sbin  sys  usr

boot  dev   etc     lib   lib64  lost+found  mnt    proc  run   srv   tmp  var

isaiah@media:/$ sudo chown -R isaiah:isaiah /docker

chown: cannot read directory '/docker/lost+found': Permission denied 
```

- Solution:
```bash
sudo find /docker -name lost+found -prune -o -exec chown isaiah:isaiah {} +
```

- Why it worked:
- ```-name lost+found -prune```: brick wall for the command. It tells the file walker: "The moment you see a folder named lost+found, drop it entirely and do not look inside."
- ```-o -exec chown...```: handles everything else, cleanly switching the ownership of your actual Docker files, containers, and configurations to isaiah without triggering that permission error.

Now we are in business!
