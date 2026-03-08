# Day 16 – Shell Scripting Basics

---

### Task 1: Your First Script
1. Create a file `hello.sh`
2. Add the shebang line `#!/bin/bash` at the top
3. Print `Hello, DevOps!` using `echo`
4. Make it executable and run it

```bash
chmod +x hello.sh
./hello.sh
```
<img width="1337" height="263" alt="image" src="https://github.com/user-attachments/assets/717051d7-db6d-4ad5-9fc9-0b9c02903cc8" />

**Document:** What happens if you remove the shebang line?

- Sometimes it still works because the shell assumes bash
- But shebang ensures the correct interpreter is used
  
---

### Task 2: Variables
1. Create `variables.sh` with:
   - A variable for your `NAME`
   - A variable for your `ROLE` (e.g., "DevOps Engineer")
   - Print: `Hello, I am <NAME> and I am a <ROLE>`

<img width="1190" height="433" alt="image" src="https://github.com/user-attachments/assets/56821a8c-8d66-4925-b5d6-ae93fe8ae9fd" />

2. Try using single quotes vs double quotes — what's the difference?

<img width="1106" height="300" alt="image" src="https://github.com/user-attachments/assets/c9918a92-98ae-4db4-9b2b-3f777d6f4df7" />

- Double quotes expands varibale
- Single quotes treat the variables as plain text
  
---

### Task 3: User Input with read
1. Create `greet.sh` that:
   - Asks the user for their name using `read`
   - Asks for their favourite tool
   - Prints: `Hello <name>, your favourite tool is <tool>`

<img width="1217" height="222" alt="image" src="https://github.com/user-attachments/assets/624cd0bc-8a63-43b8-8cfc-996e83ff8b75" />

---

### Task 4: If-Else Conditions
1. Create `check_number.sh` that:
   - Takes a number using `read`
   - Prints whether it is **positive**, **negative**, or **zero**

<img width="1306" height="396" alt="image" src="https://github.com/user-attachments/assets/febb9b85-73f1-446b-99a2-df7369737f14" />

2. Create `file_check.sh` that:
   - Asks for a filename
   - Checks if the file **exists** using `-f`
   - Prints appropriate message

<img width="1556" height="388" alt="image" src="https://github.com/user-attachments/assets/db172696-ca2d-431b-8a8f-4b87de1e4e93" />

---

### Task 5: Combine It All
Create `server_check.sh` that:
1. Stores a service name in a variable (e.g., `nginx`, `sshd`)
2. Asks the user: "Do you want to check the status? (y/n)"
3. If `y` — runs `systemctl status <service>` and prints whether it's **active** or **not**
4. If `n` — prints "Skipped."

<img width="1482" height="588" alt="image" src="https://github.com/user-attachments/assets/d2e79f8e-2180-45ed-833c-2d98bb9723fe" />

---

## Learnings

- Shebang tells the system which interpreter to use  
- Variables store values that can be reused in scripts  
- read allows interactive user input  
- if-else enables decision logic in scripts 
