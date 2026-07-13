# HomeLab---1.0
The Adventures of my Second Home lab :)
# Summary:

# Hardware Profile
- **Host System:** Dell Vostro 5890 (Desktop)
- **Motherboard:** Dell 0TG30J (UEFI v1.22.1)

### System Specs
- **OS/Kernel:** Proxmox VE (Kernel: 7.0.14-4-pve) | Base: Debian 13 (trixie)
- **CPU:** Intel Core i7-10700 (8 Cores / 16 Threads, 2.90 GHz Base / 4.80 GHz Max)
- **Memory:** 64 GB Total (Available: 62.54 GB)

### Graphics & Audio
- **iGPU:** Intel CometLake-S GT2 [UHD Graphics 630] (driver: i915)
- **dGPU:** NVIDIA GP108 [GeForce GT 1030] (driver: nouveau)
- **Audio:** Intel & NVIDIA High Definition Audio (ALSA)

### Networking
- **Ethernet:** Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet (`nic0` / `vmbr0` bridged)
- **Wireless:** Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
- **Bluetooth:** Qualcomm Atheros USB Adapter

### Storage & Partitions
- **Total Raw Storage:** 2.73 TiB
- **NVMe Drive:** Samsung SSD 970 EVO Plus 1TB (`/dev/nvme0n1`)
- **SATA SSD:** Crucial CT2000BX500SSD1 2TB (`/dev/sda`)
- **Root Partition (`/`):** 93.93 GiB (ext4 on LVM `/dev/dm-1`)
- **Swap:** 8 GiB


# Hardware - Breakdown
- Dell Vostro 5890
- System:
  - Kernel: 7.0.14-4-pve arch: x86_64 bits: 64
- *OS: Proxmox Virtual Enviroment 9.2*
- Machine:
  - Type: Desktop System: Dell product: Vostro 5890 v: N/A serial: <filter>
  - Mobo: Dell model: 0TG30J v: A00 serial: <filter> UEFI: Dell v: 1.22.1 date: 01/08/2024
- CPU:
  - Info: 8-core model: Intel Core i7-10700 bits: 64 type: MT MCP cache: L2: 2 MiB
   -Speed (MHz): avg: 800 min/max: 800/4800 cores: 1: 800 2: 800 3: 800 4: 800 5: 800 6: 800
- Graphics:
  - Device-1: Intel CometLake-S GT2 [UHD Graphics 630] driver: i915 v: kernel
  - Device-2: NVIDIA GP108 [GeForce GT 1030] driver: nouveau v: kernel
  - Display: unspecified server: N/A driver: N/A tty: 99x27
  - API: EGL v: 1.5 drivers: iris,nouveau,swrast platforms: gbm,surfaceless,device
  - API: OpenGL v: 4.6 compat-v: 4.3 vendor: mesa v: 25.0.7-2+deb13u1 note: console (EGL sourced)
    - renderer: NV138, Mesa Intel UHD Graphics 630 (CML GT2), llvmpipe (LLVM 19.1.7 256 bits)
  - Info: Tools: api: eglinfo,glxinfo x11: xdriinfo, xdpyinfo, xprop, xrandr
- Audio:
  - Device-1: Intel driver: snd_hda_intel
  - Device-2: NVIDIA GP108 High Definition Audio driver: snd_hda_intel
  - API: ALSA v: k7.0.14-4-pve status: kernel-api
- Network:
  - Device-1: Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet driver: r8169
  - IF: nic0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  - Device-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter driver: ath10k_pci
  - IF: wlp6s0 state: down mac: <filter>
  - IF-ID-1: bonding_masters state: N/A speed: N/A duplex: N/A mac: N/A
  - IF-ID-2: vmbr0 state: up speed: 1000 Mbps duplex: unknown mac: <filter>
- Bluetooth:
  - Device-1: Qualcomm Atheros driver: btusb type: USB
  - Report: rfkill ID: hci0 rfk-id: 0 state: down bt-service: not found rfk-block: hardware: no
    - software: no address: see --recommends
- Drives:
  - Local Storage: total: raw: 2.73 TiB usable: 2.67 TiB used: 11.78 GiB (0.4%)
  - ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO Plus 1TB size: 931.51 GiB
  - ID-2: /dev/sda vendor: Crucial model: CT2000BX500SSD1 size: 1.82 TiB
- Partition:
  - ID-1: / size: 93.93 GiB used: 11.77 GiB (12.5%) fs: ext4 dev: /dev/dm-1
  - ID-2: /boot/efi size: 1022 MiB used: 9 MiB (0.9%) fs: vfat dev: /dev/nvme0n1p2
- Swap:
  - ID-1: swap-1 type: partition size: 8 GiB used: 0 KiB (0.0%) dev: /dev/dm-0
- Sensors:
  - System Temperatures: cpu: 56.0 C mobo: 33.0 C gpu: nouveau temp: 41.0 C
  - Fan Speeds (rpm): cpu: 881 fan-1: 878
- Info:
  - Memory: total: 64 GiB available: 62.54 GiB used: 2.24 GiB (3.6%)
  - Processes: 396 Uptime: 34m Init: systemd Shell: Bash inxi: 3.3.38
