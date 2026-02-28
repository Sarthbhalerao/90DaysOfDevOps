# Day 26 – GitHub CLI: Manage GitHub from Your Terminal

---
### Task 1: Install and Authenticate
- 1. Install the GitHub CLI on your machine
- 2. Authenticate with your GitHub account
- 3. Verify you're logged in and check which account is active

<img width="1711" height="898" alt="image" src="https://github.com/user-attachments/assets/ff576134-42de-45dd-a59c-9985a7bd80f1" />

- 4. Answer in your notes: What authentication methods does `gh` support?
    - HTTPS (token-based)
    - SSH
    - Browser login
    - GitHub Enterprise support
      
---

### Task 2: Working with Repositories
- 1. Create a **new GitHub repo** directly from the terminal — make it public with a README
- 2. Clone a repo using `gh` instead of `git clone`
- 3. View details of one of your repos from the terminal
- 4. List all your repositories
- 5. Open a repo in your browser directly from the terminal
- 6. Delete the test repo you created (be careful!)

<img width="2148" height="1742" alt="image" src="https://github.com/user-attachments/assets/5e375f91-f7bd-4a61-b6cb-9c5df70c6719" />

---

### Task 3: Issues
- 1. Create an issue on one of your repos from the terminal — give it a title, body, and a label
- 2. List all open issues on that repo
- 3. View a specific issue by its number
- 4. Close an issue from the terminal
- 5. Answer in your notes: How could you use `gh issue` in a script or automation?
    - Auto-create issue on CI failure
    - Create issue when monitoring detects error
    - Link PR to issue automatically

 <img width="1917" height="572" alt="image" src="https://github.com/user-attachments/assets/5fddd6fe-1af1-422b-b427-59ca12b01f03" />

  
---

### Task 4: Pull Requests
- 1. Create a branch, make a change, push it, and create a **pull request** entirely from the terminal
- 2. List all open PRs on a repo
- 3. View the details of your PR — check its status, reviewers, and checks
- 4. Merge your PR from the terminal

<img width="1908" height="966" alt="image" src="https://github.com/user-attachments/assets/c551fa72-611d-4972-a938-9e56ec85424c" />

- 5. Answer in your notes:
   - **What merge methods does `gh pr merge` support?**
       - `--merge`
       - `--squash`
       - `--rebase`
   - **How would you review someone else's PR using `gh`?**
       - `gh pr checkout <number>`
       - Review changes locally
       - Comment via `gh pr review`
---

### Task 5: GitHub Actions & Workflows
- 1. List the workflow runs on any public repo that uses GitHub Actions
    - `gh run list --repo kubernetes/kubernetes`
<img width="1910" height="553" alt="image" src="https://github.com/user-attachments/assets/5d390a76-1302-48f0-94b5-3b337de6ce69" />

- 2. View the status of a specific workflow run
    - `gh run view <run-id> --repo kubernetes/kubernetes`

<img width="1562" height="542" alt="image" src="https://github.com/user-attachments/assets/7ac75513-9521-42fc-a29c-a789a24267c8" />


- 3. Answer in your notes: How could `gh run` and `gh workflow` be useful in a CI/CD pipeline?
    - Monitor pipelines
    - Auto-retry failed jobs
    - Script deployment checks
    - Automate PR approvals

---

### Task 6: Useful `gh` Tricks
Explore and try these — add the ones you find useful to your `git-commands.md`:
1. `gh api` — make raw GitHub API calls from the terminal
2. `gh gist` — create and manage GitHub Gists
3. `gh release` — create and manage releases
4. `gh alias` — create shortcuts for commands you use often
5. `gh search repos` — search GitHub repos from the terminal

---
