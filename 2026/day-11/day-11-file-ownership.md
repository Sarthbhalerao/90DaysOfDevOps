# Day 11 – File Ownership Challenge (chown & chgrp)

---
Master file and directory ownership in Linux.

- Understand file ownership (user and group)
- Change file owner using chown
- Change file group using chgrp
- Apply ownership changes recursively

---

## Task 1: Understanding Ownership (10 minutes)
- Run ls -l in your home directory
- Identify the owner and group columns
- Check who owns your files
- Format: -rw-r--r-- 1 owner group size date filename

### hands-on:

<img width="985" height="209" alt="image" src="https://github.com/user-attachments/assets/6db8b165-9bab-4ccf-80eb-da9ab665cd9c" />

---
## Task 2: Basic chown Operations (20 minutes)
- Create file devops-file.txt
- Check current owner: ls -l devops-file.txt
- Change owner to tokyo (create user if needed)
- Change owner to berlin
- Verify the changes

### hands-on:

<img width="1084" height="372" alt="image" src="https://github.com/user-attachments/assets/4c43d2dd-3ad8-4277-acee-f2c37aa0a704" />

---

## Task 3: Basic chgrp Operations (15 minutes)
- Create file team-notes.txt
- Check current group: ls -l team-notes.txt
- Create group: sudo groupadd heist-team
- Change file group to heist-team
- Verify the change

### hands-on:

<img width="1037" height="303" alt="image" src="https://github.com/user-attachments/assets/4c37834e-b680-4ede-a923-f14f7863cb10" />

---

## Task 4: Combined Owner & Group Change (15 minutes)

**Using chown you can change both owner and group together:**

- Create file project-config.yaml
- Change owner to professor AND group to heist-team (one command)
- Create directory app-logs/
- Change its owner to berlin and group to heist-team

### hands-on:

<img width="1172" height="861" alt="image" src="https://github.com/user-attachments/assets/b446eab8-2929-46b1-96dc-5d874ed4854e" />

---

## Task 5: Recursive Ownership (20 minutes)
- Create directory structure:

`mkdir -p heist-project/vault`

`mkdir -p heist-project/plans`

`touch heist-project/vault/gold.txt`

`touch heist-project/plans/strategy.conf`

- Create group planners: sudo groupadd planners
- Change ownership of entire heist-project/ directory:
  - Owner: professor
  - Group: planners
  - Use recursive flag (-R)
  - Verify all files and subdirectories changed: ls -lR heist-project/

### hands-on:

<img width="1280" height="694" alt="image" src="https://github.com/user-attachments/assets/fb3bb38d-5fb8-4672-a752-c34fe965d522" />

---

## Task 6: Practice Challenge (20 minutes)

- Create users: tokyo, berlin, nairobi (if not already created)
- Create groups: vault-team, tech-team
- Create directory: bank-heist/
- Create 3 files inside:

`touch bank-heist/access-codes.txt`

`touch bank-heist/blueprints.pdf`

`touch bank-heist/escape-plan.txt`

- Set different ownership:

- access-codes.txt → owner: tokyo, group: vault-team
- blueprints.pdf → owner: berlin, group: tech-team
- escape-plan.txt → owner: nairobi, group: vault-team
- Verify: ls -l bank-heist/

### hands-on:

<img width="1471" height="534" alt="image" src="https://github.com/user-attachments/assets/711b5768-e7fa-4a82-8368-fb6db1653671" />

---

## Commands Used

- `ls -l` – Displays detailed file information including owner, group, permissions, size, and timestamp.
- `ls -ld <directory>` – Shows detailed information about a directory itself instead of its contents.
- `ls -lR <directory>` – Recursively lists files and directories with detailed ownership and permissions.
- `id <username>` – Displays user ID (UID), group ID (GID), and group memberships of a user.
- `touch <filename>` – Creates an empty file.
- `mkdir <directory>` – Creates a new directory.
- `mkdir -p <path>` – Creates a directory along with parent directories if they don’t exist.
- `sudo useradd -m <username>` – Creates a new user with a home directory.
- `sudo groupadd <groupname>` – Creates a new group.
- `sudo chown <newowner> <filename>` – Changes the owner of a file or directory.
- `sudo chgrp <newgroup> <filename>` – Changes the group ownership of a file or directory.
- `sudo chown <owner:group> <filename>` – Changes both owner and group of a file in a single command.
- `sudo chown -R <owner:group> <directory>` – Recursively changes ownership for a directory and all its contents.

---

## What I Learned
- Ownership controls who manages a file.
- chown can change user and group together. **Syntax: sudo chown owner:group filename**
- Recursive ownership is critical for project directories.
- Incorrect ownership causes application failures.


---

















