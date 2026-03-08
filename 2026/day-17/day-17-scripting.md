# Day 17 – Shell Scripting: Loops, Arguments & Error Handling

### Task 1: For Loop
1. Create `for_loop.sh` that:
   - Loops through a list of 5 fruits and prints each one

<img width="1332" height="400" alt="image" src="https://github.com/user-attachments/assets/4bba21b7-dadc-46b6-baf0-71ac74523fac" />

2. Create `count.sh` that:
   - Prints numbers 1 to 10 using a for loop

<img width="1225" height="564" alt="image" src="https://github.com/user-attachments/assets/a439a53a-585b-41dc-9e81-1a72bf747949" />

---

### Task 2: While Loop
1. Create `countdown.sh` that:
   - Takes a number from the user
   - Counts down to 0 using a while loop
   - Prints "Done!" at the end

<img width="1182" height="678" alt="image" src="https://github.com/user-attachments/assets/7941708f-e587-4839-8183-726c9566eb99" />

---

### Task 3: Command-Line Arguments
1. Create `greet.sh` that:
   - Accepts a name as `$1`
   - Prints `Hello, <name>!`
   - If no argument is passed, prints "Usage: ./greet.sh <name>"

<img width="1522" height="420" alt="image" src="https://github.com/user-attachments/assets/19d195e4-f29e-4f3a-8f28-65a4cd164ff8" />

2. Create `args_demo.sh` that:
   - Prints total number of arguments (`$#`)
   - Prints all arguments (`$@`)
   - Prints the script name (`$0`)

<img width="1380" height="533" alt="image" src="https://github.com/user-attachments/assets/e8eefbe9-e866-4d0f-ab2d-29fb65ea97c8" />

---

### Task 4: Install Packages via Script
1. Create `install_packages.sh` that:
   - Defines a list of packages: `nginx`, `curl`, `wget`
   - Loops through the list
   - Checks if each package is installed (use `dpkg -s` or `rpm -q`)
   - Installs it if missing, skips if already present
   - Prints status for each package

> Run as root: `sudo -i` or `sudo su`

<img width="1517" height="608" alt="image" src="https://github.com/user-attachments/assets/d4729318-b2ee-4377-8766-41a14138b335" />

---

### Task 5: Error Handling
1. Create `safe_script.sh` that:
   - Uses `set -e` at the top (exit on error)
   - Tries to create a directory `/tmp/devops-test`
   - Tries to navigate into it
   - Creates a file inside
   - Uses `||` operator to print an error if any step fails

Example:
```bash
mkdir /tmp/devops-test || echo "Directory already exists"
```
<img width="1548" height="794" alt="image" src="https://github.com/user-attachments/assets/466956d1-af41-4aa7-8205-f2ea25a66c3c" />

2. Modify your `install_packages.sh` to check if the script is being run as root — exit with a message if not.

<img width="1483" height="675" alt="image" src="https://github.com/user-attachments/assets/ac2a38e5-a4f4-4c63-b04d-576340a1da7e" />

---
### Learning

- For loops automate repeated tasks
- While loops run until a condition is false
- Command-line arguments allow scripts to accept user input
- Error handling prevents scripts from silently failing
- Root checks prevent permission problems

---
