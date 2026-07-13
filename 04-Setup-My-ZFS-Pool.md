# 04 Setup My ZFS Pool
## What:
In a Proxmox homelab, ZFS acts as an all-in-one software RAID controller, volume manager, and advanced filesystem.

Instead of traditional hardware RAID (where a physical PCIe card manages your disks) or simple Linux directories, you bunch your physical drives into a ZFS Pool (called a zpool). Proxmox then carves that pool up into storage spaces for your virtual machines and containers.

## Why:
1. It Protects Against "Bit Rot" (Self-Healing)
- Over time, magnetic disks and SSDs can suffer from silent data corruption (bit rot), where a 1 flips to a 0 due to age or minor hardware glitches. Traditional systems have no idea this happened until a file crashes.

- **The ZFS Fix**: ZFS writes a cryptographic checksum alongside every piece of data. Every time a VM reads a file, ZFS recalculates the checksum. If they don't match, ZFS automatically pulls a clean copy from your redundant drive, fixes the broken block on the fly, and hands the healthy data to your VM without you ever knowing there was an issue.

2. Proxmox Cluster Replication
- If you ever expand your homelab to more than one Proxmox server, ZFS unlocks Storage Replication.

- Because ZFS tracks data blocks natively, it can instantly send incremental changes from a running VM on Node A over to Node B every few minutes. If Node A physically dies, you can boot that identical VM up on Node B almost instantly with minimal data loss.

3. Instant, Zero-Space Snapshots
- Before doing a risky software update inside a VM, you want a backup point.

- Standard directory backups have to freeze the VM and copy the massive virtual disk file.

- ZFS snapshots are instant (taking less than a second) because of its Copy-on-Write architecture. It simply freezes the existing data blocks and writes new changes to a different spot on the disk. It takes up zero extra space until your VM starts writing new data.

4. Smart RAM Caching (ARC)
- ZFS loves RAM and will automatically use your idle system memory as an ultra-fast read cache called the ARC (Adaptive Replacement Cache).

- It learns which files and boot sectors your VMs access most frequently and keeps them sitting in your fast 64GB of system RAM. This means your VMs feel incredibly snappy because they frequently bypass the slower physical SSD/HDD entirely.

## The Setup:
1. Go to Node> Disk
2. Here I have two drives total:
   - NVMe Drive: Samsung SSD 970 EVO Plus 1TB - OS/Boot Drive - ***DO NOT TOUCH***
   - SATA SSD: Crucial CT2000BX500SSD1 2TB
3. Wipe drives you intend to use in your pool(s)
   - Select Drive
   - Top middle ribbon - wipe disk
4. Goal for the future - Have two main pools:
  - Flash - where I will store my vms and containers - NVME
5. Create your bulk storage - media, image backups
  - Note: Checkout - [DiskInternals.com - Resources on the different ZFS levels](https://www.diskinternals.com/raid-recovery/zfs-raid-types/)
  
  - <img width="982" height="350" alt="image" src="https://github.com/user-attachments/assets/1935f743-29be-431f-a1c6-da1107939005" />
  
  - Currently I only have 1 drive to use for this pool so I hit *Create ZFS* select sda and hit create


## Cleaning up ```zpool list```
  - Once created you will see an updated GUI version of the ```zpool list``` command but chances are the totals reflected are not very accurate - same free as total avalible

<img width="820" height="60" alt="image" src="https://github.com/user-attachments/assets/eda82ffc-c87e-40ff-9736-dcd085a186f3" />

- With you current raid config the following command will show your total available space:
```bash
zfs list
```

<img width="298" height="56" alt="image" src="https://github.com/user-attachments/assets/d2dd408c-ffdc-458d-8c56-0c6f41a6c8b2" />

     
