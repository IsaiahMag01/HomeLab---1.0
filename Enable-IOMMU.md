# Enabling IOMMU
## What?
- PCI Pass through - allows you to pass through hd, graphics cards, etc... to your vm or lxc containers

# Make changes to your grub configurations:
1. If you do not already have a text editor... or don't like Nano(ME) install one:
  ```
  apt install vim
  ```
2. Enable IOMMU on in grub configuration file - Node -> Shell
   ```
   vim /etc/default/grub
   ```
3. Search for *Grub_CMDLINE_LINUX_DEFAULT="quiet" - I have an intel CPU so the change I need for pass through is:
  - Intel:
    ```
    intel_iommu=on
    ```
4. Save and exit:
   ```
   :wq
   ```
5. Refresh
   ```
   update-grub
   ```
6. Hit her with the old reboot
   ```
   reboot
   ```
7. Make sure everything is running correctly:
   - ### IOMMU & Hardware Passthrough Verification
   1. Check for IOMMU / DMAR Support
  ```bash
  dmesg | grep -e DMAR -e IOMMU
  ```
  - What it does: Searches the kernel ring buffer (dmesg) for Direct Memory Access Remapping (DMAR) and IOMMU logs.
  - Expected Output: You should see lines stating IOMMU enabled or DMAR: Intel-IOMMU enabled. If it returns blank, IOMMU is disabled in your system UEFI/BIOS or GRUB config.
  - ### Check for Interupt Remapping Support
  ```bash
  dmesg | grep 'remapping'
  ```
  - What it does: Filters the kernel boot logs specifically for the status of hardware interrupt translation.
  - Expected Output: Look for a line confirming AMD-Vi: Interrupt remapping enabled or Intel-IOMMU: Quirk, cannot enable interrupt remapping (or success messages like Enabled IRQ remapping). This is required for secure device isolation.

## More Info:
- [PCI Passthrough wiki](https://pve.proxmox.com/wiki/PCI_Passthrough)
  
  
   
    
