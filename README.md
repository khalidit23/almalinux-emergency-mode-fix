# 🛠️ Fixing AlmaLinux Emergency Mode: XFS Repair & Boot Recovery
  
![AlmaLinux](https://img.shields.io/badge/AlmaLinux-0073EC?style=for-the-badge&logo=almalinux&logoColor=white) 

## 🚀 Problem
During system boot, the following errors appeared:  

![img alt](https://github.com/khalidit23/almalinux-emergency-mode-fix/blob/f12e0eeeab6aaa4cb7e10e0beacc518fd897b57e/Screenshot%202025-03-23.jpeg)

## 🔍 Cause
- The **XFS log (journal)** on the root filesystem was corrupted.
- The system was using **LVM (Logical Volume Manager)**, and `/sysroot` couldn't mount properly.
 

## ✅ Solution: Fixing Emergency Mode

### ️Identify the Root Partition (LVM)

Run:
```bash
blkid
```
### Execute the following command to repair XFS:
```bash
xfs_repair /dev/mapper/almalinux-root
```
If you’re unable to repair without clearing the journal, use the `-L` flag (this will clear the journal, and may cause data loss):

```bash
xfs_repair -L /dev/mapper/almalinux-root
```
🔴 Warning: The `-L` flag clears the journal, which may cause recent data loss.

### Reboot the System

After the repair, reboot the system to check if it boots successfully:
```bash
reboot
```

## ❤️ Support
If this guide helped you, feel free to star ⭐ this repository and share it with others!
