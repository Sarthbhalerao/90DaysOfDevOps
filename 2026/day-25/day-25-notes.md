# Day 25 – Git Reset vs Revert & Branching Strategies
---

# Task 1: Git Reset — Hands-On

### 1. Make 3 commits in your practice repo (commit A, B, C)
### 2. Use `git reset --soft` to go back one commit — what happens to the changes?
  - Commit C disappears, Changes from C are still staged
<img width="1182" height="2070" alt="image" src="https://github.com/user-attachments/assets/85ff04ac-42bc-4979-ab99-b50050375ec4" />

### 3. Re-commit, then use `git reset --mixed` to go back one commit — what happens now?
  - Commit gets removed, Changes still exist, but now unstaged

<img width="987" height="576" alt="image" src="https://github.com/user-attachments/assets/73e7670c-a6f5-41cf-8fa6-0d0b7a6c8366" />

### 4. Re-commit, then use `git reset --hard` to go back one commit — what happens this time?
  - Commit removed, Changes deleted, Working directory restored

<img width="833" height="427" alt="image" src="https://github.com/user-attachments/assets/6aa88d47-f7a4-4b46-94ef-35bfc833fb59" />

### 5. Answer in your notes:

   - ## What is the difference between `--soft`, `--mixed`, and `--hard`?
       - All three move the branch pointer (HEAD) backward
       - `git reset --soft` : Moves HEAD back, Keeps changes, and Keeps them staged
           - Commit removed, but ready to recommit immediately.
       - `git reset --mixed` : Moves HEAD back, Keeps changes but unstages them
           - Commit removed, changes still in files, but not staged.
       - `git reset --hard` : Moves HEAD back, deletes changes, and restores the working directory
           - Commit removed and changes permanently deleted.
             
   - ## Which one is destructive and why?
       - `--hard` is destructive because it deletes commits from history and deletes file changes from the working directory
         
   - ## When would you use each one?
       - `--soft` : when you want to redo the last commit or you forgot add something to the commit or you want to edit commit message
       - `--mixed` : when you want to uncommit but keep changes or you want to reorganize what gets staged
       - `--hard` : when you want to completely discard local work

   - ## Should you ever use `git reset` on commits that are already pushed?
       - Reset rewrites history
       - If commits are already pushed, others may have pulled them
       - Their history will conflict
       - It forces others to fix their repo manually
    
  ---

# Task 2: Git Revert — Hands-On
### 1. Make 3 commits (commit X, Y, Z)

<img width="1102" height="645" alt="image" src="https://github.com/user-attachments/assets/a83fea4b-f13f-4259-a410-391e739261c6" />

### 2. Revert commit Y (the middle one) — what happens? 
- **Git creates a NEW commit, that undoes Y**

<img width="1175" height="778" alt="image" src="https://github.com/user-attachments/assets/bed0a9f6-ce18-469c-b33a-6ae5b46c4557" />

### 3. Check `git log` — is commit Y still in the history? 
- **YES**

<img width="1111" height="693" alt="image" src="https://github.com/user-attachments/assets/ad558c9c-f649-4e8b-9e84-ebb3f852542c" />


### 4. Answer in your notes:
   - ## How is `git revert` different from `git reset`?
   - `git revert` creates a new commit that revers changes, but `git reset` rewrites history
   - ## Why is revert considered **safer** than reset for shared branches?
       - Creates a new commit that undoes changes from a previous commit.
       - Does NOT rewrite history.
       - Safe for branches shared with others (like main, develop, production branches).

   - ## When would you use revert vs reset?
       - `revert` can be used when you are working on , shared branch, on prod or whe you are fixing main branch
       - `rset` can be used when you are working locally and no commits are pushed and you want to cleanup commits before oushing

---

# Task 3: Reset vs Revert — Summary
Create a comparison in your notes:

| | `git reset` | `git revert` |
|---|---|---|
| Removes commit from history? | YES | NO |
| Creates new commit? | NO | YES |
| Safe for shared/pushed branches? | NO | YES |
| When to use | LOCAL CLEANUP | UNDO PUSH COMMITS |

---

# Task 4: Branching Strategies


## 1. **GitFlow** — main, develop, feature, release, hotfix branches
- GitFlow enables parallel development using multiple long-lived and short-lived branches. It separates development, release preparation, and hotfixes clearly.
- **Branches**
    - **main (or master) →** Used for product release.
    - **develop →** Used for ongoing development.
    - **feature →** Created from the develop branch to work on specific features.
    - **release →** Created from the develop branch to prepare for production releases and bug fixes.
    - **hotfix →** Created from the master branch to address urgent issues directly in production.

<img width="1536" height="1024" alt="554c0fcc-d352-4336-9d27-7b7fbf64ce5f" src="https://github.com/user-attachments/assets/7a7f8fe9-6e06-4c09-b3fd-663ac2e9370e" />

- **When / Where It’s Used**
    - Large teams
    - Enterprise environments
    - Scheduled version releases
    - Products with long maintenance cycles
    - Regulated industries

- **Pros:**
    - Enables parallel development
    - Stable production branch
    - Supports multiple versions
    - Clear bug & hotfix process
    - Strong release management structure

- **Cons:**
    - Complex branch structure
    - Multi-step merges
    - Harder debugging due to history
    - Slower releases
    - Not ideal for CI/CD-heavy teams
 
## 2. **GitHub Flow** — simple, single main branch + feature branches

- A lightweight workflow where:
    - main is always deployable
    - Feature branches are short-lived
    - Changes are merged via Pull Requests
    - No release branches. No develop branch.

- **Branches**
    - **main (or master) →** Stable production-ready code
    - **feature →** Feature or bug-fix branches

<img width="1536" height="1024" alt="1b0868fe-efb2-4b2b-8be9-02541c2e5c00" src="https://github.com/user-attachments/assets/1de2781e-ab19-4298-b807-d91ec92e3f50" />

- **When / Where It’s Used**
    - Startups
    - Small teams
    - SaaS products
    - Web applications
    - Continuous Deployment environments

- **Pros:**
    - Simple & easy to understand
    - Fast releases
    - Great for CI/CD
    - Encourages short production cycles
    - Ideal for small teams

- **Cons:**
    - Not ideal for managing multiple versions
    - Risk of unstable production if testing is weak
    - Everyone merges into main (can cause conflicts in big teams)
    - Harder to maintain legacy versions

## 3. **GitLab Flow** — GitLab Flow combines Structured release branches (like GitFlow) & Continuous development (like GitHub Flow). It keeps production stable while allowing CI/CD flexibility.

- **Branches**
    - **main/master →** Main production branch housing stable release ready code
    - **develop →** Contains new features and bug fixes.
    - **feature →** Feature branches are created from the develop branch to work on new features or fixes, then merged back into develop
    - **release →** A release branch is created from develop to prepare a new release and later merged into both develop and main branches.

<img width="1536" height="1024" alt="d72b4b0b-d4f8-43f8-b823-c6352225f51c" src="https://github.com/user-attachments/assets/3b559437-0bd3-457c-bb33-343def379bad" />

- **When / Where It’s Used**
    - Medium to large teams
    - Teams using GitLab CI/CD
    - Projects needing controlled releases + CI

- **Pros:**
    - Scalable
    - Balanced structure
    - Supports CI/CD
    - Prevents accidental production changes
    - Allows parallel development

- **Cons**
    - More complex than GitHub Flow
    - Feature drift risk
    - Can slow down urgent releases
    - Learning curve for beginners

## 4. **Trunk-Based Development** — everyone commits to main, short-lived branches
- Trunk-Based Development is a branching strategy where all developers work directly on a single main branch, keeping it always in a release-ready state.
    - No long-lived branches
    - Short-lived branches (1–2 days max)
    - Feature flags hide incomplete work
    - Strong CI/CD required

<img width="1536" height="1024" alt="d7ff98b3-9930-444d-bfde-59fcee64f3c4" src="https://github.com/user-attachments/assets/72778de2-4dd8-4c41-b36c-261c1476b9cd" />

- **When / Where It’s Used**
    - Teams with strong CI/CD
    - Experienced developers
    - Continuous deployment environments
    - Microservices architecture

- **Pros:**
    - Minimal merge conflicts
    - Faster integration
    - High visibility of changes

- **Cons:**
    - Requires disciplined team
    - Needs strong automated testing
    - Hard for very large teams

---

- **Which strategy would you use for a startup shipping fast?**
    - GitHub Flow
      
- **Which strategy would you use for a large team with scheduled releases?**
    - Git Flow

- **Which one does your favorite open-source project use? (check any repo on GitHub)**
    - Example: Kubernetes
    - Kubernetes uses:
        - main branch
        - Release branches (release-1.xx)
        - Feature development via PR
        - This is closer to **GitHub Flow + Release Branches** (Hybrid Model)


---

### Task 5: Git Commands Reference Update

- git command cheat-sheet updated in repo https://github.com/Sarthbhalerao/cheat-sheets

---
