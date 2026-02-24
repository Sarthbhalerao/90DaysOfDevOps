# Day 24 – Advanced Git: Merge, Rebase, Stash & Cherry Pick
---
## Challenge Tasks

### Task 1: Git Merge — Hands-On
1. Create a new branch `feature-login` from `main`, add a couple of commits to it
2. Switch back to `main` and merge `feature-login` into `main`
3. Observe the merge — did Git do a **fast-forward** merge or a **merge commit**?
4. Now create another branch `feature-signup`, add commits to it — but also add a commit to `main` before merging
5. Merge `feature-signup` into `main` — what happens this time?

<img width="852" height="966" alt="image" src="https://github.com/user-attachments/assets/93dff872-1c89-4703-8891-2ccc023122ae" />

6. Answer in your notes:
   - **What is a fast-forward merge?**
       - fast-forward merge occurs when no new commits exist on the target branch, so Git simply moves the branch pointer ahead without creating a merge commit.
   - **When does Git create a merge commit instead?**
       - Merge commit happens when both branches have diverged.
   - **What is a merge conflict? (try creating one intentionally by editing the same line in both branches)**
       - Merge conflict occurs when same part of file changed differently in two branches
  
<img width="798" height="1046" alt="image" src="https://github.com/user-attachments/assets/a531998e-a9f8-46fc-88b9-a3e8f5c6950b" />

---

### Task 2: Git Rebase — Hands-On
1. Create a branch `feature-dashboard` from `main`, add 2-3 commits
2. While on `main`, add a new commit (so `main` moves ahead)
3. Switch to `feature-dashboard` and rebase it onto `main`
4. Observe your `git log --oneline --graph --all` — how does the history look compared to a merge?
5. Answer in your notes:
   - What does rebase actually do to your commits?
   - How is the history different from a merge?
   - Why should you **never rebase commits that have been pushed and shared** with others?
   - When would you use rebase vs merge?

