# Day 13 – Linux Volume Management (LVM)

---

## Challenge Tasks

## Task 1: Check Current Storage

- Run: lsblk, pvs, vgs, lvs, df -h

<img width="1435" height="648" alt="image" src="https://github.com/user-attachments/assets/ea18cd41-b2a6-4174-af02-c7030dfb52f4" />

---
## Task 2: Create Physical Volume

- `pvcreate /dev/nvme2n1e` : Initializes a disk as an LVM physical volume.  
- `pvs` : Displays all available physical volumes in the system.

<img width="1196" height="142" alt="image" src="https://github.com/user-attachments/assets/8d12c391-3d53-40c8-9b2c-2022fcdcf84f" />

---

## Task 3: Create Volume Group

- `vgcreate lvm_tutorial /dev/nvme2n1` : Creates a new volume group named devops-vg using the specified physical volume.  
- `vgs` : Displays information about all volume groups.  

<img width="1443" height="457" alt="image" src="https://github.com/user-attachments/assets/0e46d3c1-3bbb-4b81-8133-bf1fb7a94f89" />

---

## Task 4: Create Logical Volume

- `lvcreate -L 1G -n lv_1 lvm_tutorial` : Creates a 500MB logical volume named app-data inside devops-vg.  
- `lvs` : Displays all logical volumes in the system.  

<img width="1649" height="1814" alt="image" src="https://github.com/user-attachments/assets/11cb430b-e052-41e4-a6e2-eab3ebe89714" />
<img width="1592" height="512" alt="image" src="https://github.com/user-attachments/assets/3853951e-6f47-4562-90c8-8cbe11c12594" />

---

## Task 5: Format and Mount
- `mkfs -t ext4 /dev/lvm_tutorial/lv_1` : Formats the logical volume with the ext4 filesystem.  
- `mkdir /mnt/lv_1_Devops` : Creates a mount directory for the logical volume. 
- `mount /dev/lvm_tutorial/lv_1 /mnt/lv_1_Devops/` : Mounts the logical volume to the specified directory. 
- `df -h /mnt/app-data` : Displays disk usage of the mounted logical volume in human-readable format. 

<img width="1439" height="1146" alt="image" src="https://github.com/user-attachments/assets/3bef329c-c4bd-4200-8e37-bc3ac80c077e" />

---

## Task 6: Extend the Volume
- `lvextend -L +200M /dev/devops-vg/app-data` : Extends the logical volume size by an additional 200MB.  
- `resize2fs /dev/devops-vg/app-data` : Resizes the filesystem to utilize the newly added space.  
- `df -h /mnt/lv_1_Devops/` : Verifies the updated disk size after extending the volume.  

<img width="1868" height="989" alt="image" src="https://github.com/user-attachments/assets/f3194e8c-ae20-41c7-a1e9-891db56f21b6" />

<img width="999" height="94" alt="image" src="https://github.com/user-attachments/assets/ff74b7ec-440d-4d9d-b908-61471c18c568" />

---

## What I Learned
- LVM allows flexible storage management.
- Logical volumes can be extended without unmounting.
- Storage is structured as PV → VG → LV.
- Filesystem must be resized after extending a logical volume.

- ---
