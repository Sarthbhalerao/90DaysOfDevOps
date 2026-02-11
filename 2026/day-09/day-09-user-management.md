# 🐧Day 09 – Linux User & Group Management Challenge
---
## 🐧Today's goal is to practice user and group management by completing hands-on challenges.

### Figure out how to:

- Create users and set passwords
- Create groups and assign users
- Set up shared directories with group permissions
---

## 🐧Users & Groups Created
- Users: tokyo, berlin, professor, nairobi
  
  <img width="1587" height="506" alt="image" src="https://github.com/user-attachments/assets/9a67a269-e693-48df-9726-3804316cd2d6" />

- Groups: developers, admins, project-team

<img width="1687" height="200" alt="image" src="https://github.com/user-attachments/assets/ced31bec-faba-48e6-b830-8784d904689a" />

--- 

## 🐧Group Assignments
- tokyo → developers, project-team
- berlin → developers, admins
- professor → admins
- nairobi → project-team

<img width="1665" height="530" alt="image" src="https://github.com/user-attachments/assets/07d955ef-75cf-47ed-8ce9-9c8bdd7c8a1c" />

---

## 🐧Directories Created
- /opt/dev-project (developers, 775)
- /opt/team-workspace (project-team, 775)

<img width="1673" height="1046" alt="image" src="https://github.com/user-attachments/assets/3819c6fb-d5be-4bb8-ab1b-f117699f1e53" />

---
## 🐧Test cases

- Test by creating files as **tokyo and berlin**

<img width="1529" height="465" alt="image" src="https://github.com/user-attachments/assets/fbb45c6e-6a98-4d91-b001-64188b90c658" />

- Test by creating file as **nairobi**

<img width="1525" height="175" alt="image" src="https://github.com/user-attachments/assets/c091e7bf-46c2-45f8-8ef3-9138d79a859f" />

---

## 🐧Commands Used
- `useradd -m <username>` : create a user with home directory
- `passwd <username>` : set / update the user password.
- `cat /etc/passwd` : Display all system user and their account detils.
- `whoami` : shows the current user
- `groupadd <groupname>` : create a new group
- `cat /etc/group` : Displays all system groups and their members.
- `usermod -aG <groupname> <username>` : Adds a user to a group without removing them from existing groups.
- `groups <username>` : Displays all groups a specific user belongs to.
- `chgrp <groupname> </path>` : Changes the group ownership of a file or directory
- `chmod 775 </path>` : Sets permissions to rwxrwxr-x (owner and group full access, others read & execute).
- `ls -ld </path>` : Displays detailed information about the directory itself (not its contents).
- `sudo -u <username> <command>` : Executes a command as another user to test access permissions. 

---

## 🐧What I Learned
- How Linux manages multiple users and groups
- Importance of group permissions for shared access
- How to safely test access using sudo -u

---
