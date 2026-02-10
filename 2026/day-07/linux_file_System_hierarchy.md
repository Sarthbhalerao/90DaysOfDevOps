# 🐧 Linux File System Hierarchy

In Linux, everything is treated as a **file**, including hardware devices.  
Files are organized inside **directories**, forming a **tree structure** known as the **Linux File System Hierarchy**.

Linux follows a **single-rooted, inverted tree structure**, where the **root directory (`/`)** is the top-level directory and the starting point of everything.

---

## 📁 `/` – Root Directory
- Base of the Linux file system  
- Starting point of all directories  
- Represented by a forward slash `/`
- I would use this when I need to navigate the base of the entire Linux system or reference any directory using an absolute path.
---

## 📁 `/root`
- Home directory of the **root (superuser)**  
- Different from `/home`
- I would use this when I’m logged in as the root user and need to access root-specific files or scripts.
---

## 📁 `/bin` – User Binaries
- Contains essential user commands  
- Required for system operation (even in single-user mode)  
- Examples:
  - `ls`
  - `cp`
  - `cat`
  - `mv`
- I would use this when I want to run essential commands like ls, cp, or cat that must be available even in recovery mode.
---

## 📁 `/sbin` – System Binaries
- Contains system administration commands  
- Mainly used by **root/admin users**  
- Examples:
  - `iptables`
  - `reboot`
  - `fdisk`
  - `fsck`
- I would use this when I’m performing system administration tasks such as disk repair, rebooting, or configuring networking.
---

## 📁 `/dev` – Device Files
- Contains files representing hardware devices  
- Includes disks, terminals, USB devices, etc.  
- Examples:
  - `/dev/tty`
  - `/dev/sda`
- I would use this when I need to identify or interact with hardware devices like disks, terminals, or USB drives.
---

## 📁 `/var` – Variable Files
- Stores files that **change frequently**  
- Includes logs and runtime data  

### Common Subdirectories:
- `/var/log` → System and application logs  
- `/var/lib` → Databases and package data  
- `/var/mail` → User mailboxes  
- `/var/tmp` → Temporary files (persist after reboot)
- I would use this when I’m checking logs, troubleshooting issues, or monitoring data that changes frequently.
---

## 📁 `/mnt` – Mount Directory
- Used to temporarily mount file systems manually
- I would use this when I temporarily mount a filesystem for testing or manual access.
---

## 📁 `/media` – Removable Media
- Mount point for removable devices  
- Examples:
  - USB drives  
  - CD/DVD  
  - External hard drives  
- I would use this when I plug in a USB drive or external disk and want to access its contents.
---

## 📁 `/usr` – User Applications
- Contains user-installed applications and libraries  
- Not critical for system boot  
- Most user-level programs live here
- I would use this when I’m working with installed software and libraries that are not critical for system boot.
---

## 📁 `/etc` – Configuration Files
- Stores system and application configuration files  
- Controls system behavior and services  
- Contains startup and shutdown scripts
- I would use this when I need to navigate the base of the entire Linux system or reference any directory using an absolute path

---

## 📁 `/boot` – Boot Loader Files
- Files required to boot the Linux system  
- Contains:
  - GRUB boot loader  
  - Linux kernel files
  - I would use this when I’m troubleshooting boot issues or managing kernel and bootloader settings.

---

## 📁 `/opt` – Optional Applications
- Used for third-party or optional software  
- Software code is usually stored in `/opt`
- Binary files are often linked to `/bin` so all users can run them
- I would use this when I install third-party or vendor-provided software outside the system package manager.

---

## 📁 `/home` – Home Directory
- Contains home directories of normal users  
- Example:
  - `/home/user1`
  - `/home/user2`
- I would use this when I manage user files, permissions, or user-specific configurations.

---

## 📁 `/tmp` – Temporary Files
- Stores temporary files created by system and users  
- Automatically cleared on reboot
- I would use this when I need a location for short-lived files that can safely be deleted after reboot.

---

## 🐧 Summary
Understanding the Linux file system hierarchy is essential for:
- System administration  
- Troubleshooting  
- DevOps and cloud operations  

This structure helps Linux remain **organized, secure, and efficient**.
