# 08 Setup Samba Share

1. ```sudo apt install samba```
2. ```sudo apt install vim```
3. Create backup of initial configuration file:
   ```bash
   cd /etc/samba
   sudo mv smb.conf smb.conf.old
   ```
4. Edit the samba config
   ```bash
   sudo vim smb.conf
   ```
5. Paste the following:
```bash
[global]
   server string = Media - Match the server
   workgroup = WORKGROUP
   security = user - require user to be connected
   map to guest = Bad User - guest cannot do it
   name resolve order = bcast host
   hosts allow = 192.168.1.1/24 - if not same ip cannot
   hosts deny = 0.0.0.0/0 - everyone else denied

[data]
   path = /data
   force user = youruser
   force group = youruser
   create mask = 0774 - user group read righ texecute
   force create mode = 0774
   directory mask = 0775
   force directory mode = 0775
   browseable = yes
   writable = yes
   read only = no
   guest ok = no

[docker]
   path = /docker
   force user = youruser
   force group = youruser
   create mask = 0774
   force create mode = 0774:w
   directory mask = 0775
   force directory mode = 0775
   browseable = yes
   writable = yes
   read only = no
   guest ok = no
```

6. Set services to auto start on reboot:
```bash
sudo systemctl enable smbd
sudo systemctl enable nmbd
sudo systemctl restart smbd
sudo systemctl restart nmbd
```

7. Add yoru samba user:
```bash
sudo smbpasswd -a youruser
```

Should be able to auto connect on mac from here...

## Setup windows auto discover tool
1. Install wsdd
```bash
sudo apt install wsdd
```
2. When you open the discover page on your windows machine should now see this here!

Ran into an issue I was having where I could not connnect! Windows could not find the steps:

Cleared DNS cache
changed network settings
made my pc open to public folders
Nothing was working!

Thank i realized to check there server!!
In the config file:
<img width="592" height="30" alt="image" src="https://github.com/user-attachments/assets/35bdc35d-af3a-4b40-a1ae-5dd2981530f7" />
if you do not have the correct ranges you cannot connect - duh, I was off by one ssid octet, now I am able to connect!
