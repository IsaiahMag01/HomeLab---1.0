- Inital Steps - System Was Origionally running my TrueNAS server but changing living situations decieded I would leave behind one of my old desktops that was much larger in favor of a Dell Vostro 5890 that I bought off a friend in 2025
# Step 1 Setup:
1. Added Proxmox to one of my Ventoy USB that I keep on hand with update Linux and Windwos Iso
2. Verified all hardrives and components were seeded and cleared up
3. Pulled an ethernet cable from the living room about 300 feet into my room where I had a web of wires to connect the vostro to power, plus reach the very end of the Cat 8 Cable and also connect to my monitor, Keyboard and mouse - was nowhere to move
# The adventures of flashing - 4th times the try
1. Pluged in my drive
2. Booted to the ISO
3. Completed inital setup:
   1. Selected my 1tb NVME
   2. Set email and root password
   3. Configured my network - reserved 30-40 for this homelab
   4. Set homelab to .30
   5. Completed initual configuration
   6. Than the fun began... after about 5 minutes of loading rebooted
   7. Error... Couldn't find the kernal
   8. Rebooted agian, and again... Couldn't find the kernal
4. For roughly an hour reinstalled 3x, jumped into the command line - was a bit of a pain to do especially becuase Gemini was not much of a help - could see the kernal was there! Just couldn't get the system to touch it!
5. Eventually switched over to my laptop - good old FedoraOS - reinstalled Proxmox Virtual Server
6. Finnally it worked!!!!
7. Watched a couple of videos to get my bearings and create some containers than ran out of time to keep messing with it... this was In May I beleive

======================================
Here we are again in July 2026!!!
======================================
