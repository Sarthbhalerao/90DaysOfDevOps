# Day 10 – File Permissions & File Operations Challenge

---

## Master file permissions and basic file operations in Linux.

- Create and read files using touch, cat, vim
- Understand and modify permissions using chmod

---

## Files Created
- devops.txt
- notes.txt
- script.sh
- project/

<img width="1433" height="313" alt="image" src="https://github.com/user-attachments/assets/1f98031d-c2b0-49a2-aa0d-fde819a2007e" />

# Read Files

- Display first 5 lines of `/etc/passwd` using `head`
- Display last 5 lines of `/etc/passwd` using `tail`
  
<img width="1398" height="390" alt="image" src="https://github.com/user-attachments/assets/a44fa839-bc08-4864-bf91-3477fc7ac7d7" />

--- 
# Understand Permission

<img width="1839" height="672" alt="image" src="https://github.com/user-attachments/assets/a010fd63-8c22-4220-ad9e-5226310b1ebd" />

---

## Permission Changes

- **script.sh** : Make it execuatable
    - **Before:** -rw-rw-r-- 
    - **After:**  -rwxrwxr-x

- **devops.txt** : Make devops.txt read-only
    - **Before:** -rw-rw-r--
    - **After:**  -r--r--r--

- **notes.txt** : Set notes.txt to 640 (owner: rw, group: r, others: none)
    - **Before:** -rw-rw-r--
    - **After:**  -rw-r-----

- **Create directory project/ with permissions 755**
    - **Permissions:** drwxr-xr-x (755)

<img width="781" height="963" alt="image" src="https://github.com/user-attachments/assets/3c366fe3-843a-4a4b-a1a0-648b2b5e996f" />

---

## Commands Used
- **touch devops.txt** : Creates an empty file.

- **echo "text" > notes.txt** : Writes text to a file (overwrites existing content).

- **echo "text" >> devops.txt** : Appends text to a file without overwriting existing content.

- **cat > notes.txt** : Creates a file and allows manual content entry from the terminal.

- **vim script.sh** : Opens or creates a file using the Vim editor.

- **vim -R script.sh** : Opens a file in Vim in read-only mode.

- **ls -l** : Displays detailed file information including permissions, owner, group, size, and timestamp.

- **ls -ld project** : Displays detailed information about the directory itself instead of its contents.

- **cat notes.txt** : Displays the entire contents of a file.

- **head -n 5 /etc/passwd** : Displays the first 5 lines of a file.

- **tail -n 5 /etc/passwd** : Displays the last 5 lines of a file.

- **chmod +x script.sh** : Adds execute permission to a file.

- **chmod -x script.sh** : Removes execute permission from a file.

- **chmod a-w devops.txt** : Removes write permission for all users (owner, group, and others).

- **chmod 640 notes.txt** : Sets file permissions numerically (owner: read & write, group: read, others: none).

- **chmod 755 project** : Sets directory permissions to rwxr-xr-x.

- **mkdir project** : Creates a new directory.

- **./script.sh** : Executes a script located in the current directory.
- **ls -l** : List all files with all the details including permission, owner, group etc.

---

# What I Learned
- How Linux permission structure works (owner/group/others)
- Difference between symbolic and numeric chmod
- Why execute permission is required for scripts\
  
---
