# Day 13 – Linux Volume Management (LVM)

---

## Challenge Tasks

### Task 1: Check Current Storage

- `lsblk` (List Block Devices): Shows all disks, partitions, and mount points.

<img width="1276" height="441" alt="image" src="https://github.com/user-attachments/assets/7b019b68-c886-466e-b874-c9638f21551d" />

- `df -h` (Disk free in human-readable form): Shows filesystem usage.

<img width="1098" height="279" alt="image" src="https://github.com/user-attachments/assets/5ed198b8-1b1f-47c7-85e4-0cfa5cec64c9" />


---

### Task 2 – Create Physical Volume
- Go to AWS console under **Elastic Block Store --> Voume --> Create Volume**
  
<img width="1917" height="1019" alt="image" src="https://github.com/user-attachments/assets/390ddd57-a6e5-4be0-8e01-896c688b6686" />

- Fille the details
  
<img width="1917" height="1533" alt="image" src="https://github.com/user-attachments/assets/dd9d2a1e-8afa-481a-ac4d-6823f0b8a88c" />

- Create and attach r=the volume.
  
<img width="1918" height="764" alt="image" src="https://github.com/user-attachments/assets/85f37d59-ab31-4b4e-b335-b8df7beb5dd7" />

- select the proper device name
  
<img width="1920" height="1110" alt="image" src="https://github.com/user-attachments/assets/b3fc9d18-8248-41ca-a242-04c6affc6f09" />

<img width="3829" height="628" alt="image" src="https://github.com/user-attachments/assets/eac5f819-763c-46c2-ae53-272df035077c" />

- Verify if volume is atatched or not using `lsblk`

<img width="896" height="366" alt="image" src="https://github.com/user-attachments/assets/d074d4f3-9b27-41f5-a7ac-40157bb68acb" />

---

## Format and Mount

- Format - `mkfs -t ext4 /dev/nvme1n1`

- mount drive `mount /dev/nvme1n1 /mnt/data/`

<img width="1273" height="1051" alt="image" src="https://github.com/user-attachments/assets/27399fe1-78f0-480e-8f42-55e07eb2a846" />

## auto mount

- vim /etc/fstab

<img width="1357" height="182" alt="image" src="https://github.com/user-attachments/assets/4e1141d0-6efd-4a43-98e7-2ad6e83c0296" />



