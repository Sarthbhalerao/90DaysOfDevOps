# Part 1 – Install & Configure Git

- Verify Git is installed on your machine
    - `git --version` or use `sudo apt install git -y` to install if not found
- Set up your Git identity — name and email
    - `git config --global user.name "Your Name"` To set your global git user name
    - `git config --global user.email "your@email.com"` To set your email

- Verify your configuration
    - `git config --list` verify your identity, Git uses it to label commits.

  <img width="1173" height="310" alt="image" src="https://github.com/user-attachments/assets/125f4bac-f770-420f-85c4-ad6a4e82946a" />

---

# Task 2: Create Your Git Project

- Create a new folder called devops-git-practice
    - `mkdir devops-git-practice` to create directory
- Initialize it as a Git repository
  - `git init` Initialize this folder as a git repository
- Check the status — read and understand what Git is telling you
    - `git ststus` --> It will show branch name , and commit details
- Explore the hidden `.git/` directory — look at what's inside
    - `ls -la` To list hiddent files
    - `cd .git/` to get into `.git/` folder

- `.git/` stores the entire repository history and metadata.

<img width="1470" height="812" alt="image" src="https://github.com/user-attachments/assets/39f2c46b-4fc8-41a1-8239-3e53d636784e" />

---

# Task 3: Create Your Git Commands Reference

- Create a file called git-commands.md inside the repo
- Add the Git commands you've used so far, organized by category:
- Setup & Config
- Basic Workflow Viewing Changes For each command, write: What it does (1 line), An example of how to use it

<img width="1358" height="318" alt="image" src="https://github.com/user-attachments/assets/addb6e7e-a254-448a-bb77-01697171339f" />

---

# Task 4: Stage and Commit

- Stage your file
    - `git add <file_name>` : Stage your file.
- Check what's staged
    - `git status` : check staged files.
- Commit with a meaningful message
    - `git commit -m "commit message"` : commit your changes.
- View your commit history
    - `git log` : view history

<img width="1503" height="940" alt="image" src="https://github.com/user-attachments/assets/bedd2823-b4fd-487e-821d-8fe88584ec38" />

---

# Task 5: Make More Changes and Build History

- Edit `git-commands.md` — add more commands as you discover them
- Check what changed since your last commit
- Stage and commit again with a different, descriptive message
- Repeat this process at least 3 times so you have multiple commits in your history
- View the full history in a compact format

- `git diff` : see the changes
  
<img width="1469" height="698" alt="image" src="https://github.com/user-attachments/assets/9e55a0f9-2b67-4b49-b07a-d21e96ec3504" />

---

# Task 6: Understand the Git Workflow

## What is the difference between git add and git commit?

- add → moves changes to staging area
- commit → saves staged changes to repository history
  
## What does the staging area do? Why doesn't Git just commit directly?

- It lets you choose exactly what changes to commit.
  
## What information does git log show you?

- Commit ID, author, date, message.
  
## What is the .git/ folder and what happens if you delete it?

- It stores all commit history and repository metadata. Deleting it removes version control.
  
## What is the difference between a working directory, staging area, and repository?

- **Working directory →** your actual files
- **Staging area →** selected changes ready to commit
- **Repository →** committed history

---
