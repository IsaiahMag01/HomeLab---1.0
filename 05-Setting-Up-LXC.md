# 05 Setting Up LXC
## What for us?
- Main container which will host:
  - Data
  - Servar apps
  - Jellyfin
  - Music
  - Ebooks
  - etc
 
## Get Container Template
1. Go to local
2. Go to CT Templates > templates on ribon
3. Select Ubuntu - or your most used distro
4. Select ubuntu-22.04-Standard
5. Once say "Task Ok" you are good to go!

## Setup Container:
1. Create Container - Top Right
2. Keep your node unless you have mult
3. Set CTID to whatever makes sense to you
4. Set your host name - Media
5. Keep the following checked:
  - Unprivialged container
  - Nesting
6. Set the password for your container - I persionally use a password manager (Proton cough cough...)
7. Move to templates - use your chosen tempalte - I chose Ubuntu
8. Setup disk
- I stored my disk in local-lvm
- Not where you are storing the content itself... that will go in your ZFS pool... this will be where your applications and configs are stored
  - NOTE: Depending on your media your config can get pretty big so judge acordingly
- I chose - 80GB
9. Setup CPU
- I Chose 4 Cores
10. Setup memmory
- 8192 - about 8 gigs of memory
- 2048 - about 2 gigs of swap memory
11. Setup Network
- Go to the first option - IPv4 and set yoru ip... 2 options DHCP(dynamic ip handeled by your router), static (you set - do this one)
- I set my ip - static
12. Skip DNS
13. Finish and wait for the "Task OK"
