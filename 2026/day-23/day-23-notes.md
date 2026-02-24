# Task 1: Understanding Branches
---

### What is a branch in Git?
- A branch is a parallel line of development. It allows developers to build features without affecting the main branch.

### Why do we use branches instead of committing everything to main?
- To avoid risk of breaking stable code in the main branch

### What is HEAD in Git?
- HEAD is a pointer to the currently checked-out branch/commit.
  
### What happens to your files when you switch branches?
- Git updates your working directory to match that branch’s snapshot

---

### Task 2: Branching Commands — Hands-On
In your `devops-git-practice` repo, perform the following:
1. List all branches in your repo
2. Create a new branch called `feature-1`
3. Switch to `feature-1`
4. Create a new branch and switch to it in a single command — call it `feature-2`
5. Try using `git switch` to move between branches — how is it different from `git checkout`?

<img width="1389" height="557" alt="image" src="https://github.com/user-attachments/assets/330f91ed-2974-49f9-94c9-a27e26cfd4b3" />

  - `git switch` : It is ONLY for switching branches
  - `git checkout` : git checkout does multiple things (switch branches, create & switch branch, checkout specific commits)

6. Make a commit on `feature-1` that does **not** exist on `main`

<img width="1412" height="933" alt="image" src="https://github.com/user-attachments/assets/fb6ef250-dc48-454d-a598-14cc808c596d" />

7. Switch back to `main` — verify that the commit from `feature-1` is not there

<img width="1227" height="745" alt="image" src="https://github.com/user-attachments/assets/da935ac2-2194-4fed-ad84-70dc70cc8338" />

8. Delete a branch you no longer need

<img width="1283" height="113" alt="image" src="https://github.com/user-attachments/assets/3b4dbd07-c26c-45b2-a621-716b1982fc5c" />

9. Add all branching commands to your `git-commands.md` (added in another repo "cheat-sheets")

<img width="1589" height="813" alt="image" src="https://github.com/user-attachments/assets/6fbbc955-517a-40f5-90db-9726b0effa4b" />

---

### Task 3: Push to GitHub
1. Create a **new repository** on GitHub (do NOT initialize it with a README)

<img width="1901" height="1870" alt="image" src="https://github.com/user-attachments/assets/4c49851f-8fe6-445b-9c39-a64ce22220a5" />

2. Connect your local `devops-git-practice` repo to the GitHub remote

<img width="1577" height="346" alt="image" src="https://github.com/user-attachments/assets/a4c3b29d-4ede-496c-8f9d-d8d6c1b40065" />

3. Push your `main` branch to GitHub
4. Push `feature-1` branch to GitHub
5. Verify both branches are visible on GitHub

<img width="1892" height="1158" alt="image" src="https://github.com/user-attachments/assets/091869f2-de57-4b73-8516-a48e540e4793" />

6. Answer in your notes: What is the difference between `origin` and `upstream`?

- origin - means remote repository
- upstream - original repository you forked from

---

### Task 4: Pull from GitHub
1. Make a change to a file **directly on GitHub** (use the GitHub editor)
2. Pull that change to your local repo

<img width="1011" height="483" alt="image" src="https://github.com/user-attachments/assets/0815abe8-38fa-4064-a877-04866e43c93c" />

3. Answer in your notes: What is the difference between `git fetch` and `git pull`?

  - fetch = downloads changes but doesn’t merge
  - pull = fetch + merge

---

### Task 5: Clone vs Fork
1. **Clone** any public repository from GitHub to your local machine

<img width="1445" height="261" alt="image" src="https://github.com/user-attachments/assets/477b7eb8-cfea-4197-af93-3fe7a5c23c61" />

2. **Fork** the same repository on GitHub, then clone your fork

<img width="1915" height="1336" alt="image" src="https://github.com/user-attachments/assets/d4b9846b-916d-40a5-acf4-c046c632b043" />

---

### 3. Answer in your notes:

   - **What is the difference between clone and fork?**
       - **clone** : create a local copy of a repo
       - **fork** : create a copy of that repo in your github account.
   - **When would you clone vs fork?**
       - **clone** : for exploring or internal practice
       - **fork** : when you want to contribute to someone else's project.
   - **After forking, how do you keep your fork in sync with the original repo?**
       - Click on the **sync fork** button on your git UI 
---
