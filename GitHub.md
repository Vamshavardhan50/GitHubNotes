# 🚀 Ultimate Git & GitHub Cheatsheet

A simple, powerful guide to mastering version control. From your first commit to open-source contributions.

---

## 1. Setting Up (Start Here)
Before you do anything, you need a repository.

```bash
# Turn your current folder into a Git repository
git init

# OR: Download an existing repository from GitHub to your computer
git clone <url_of_repo>
```

## 2. The Daily Workflow
The 3 steps you will repeat 90% of the time.

1.  **Check Status:** See what files changed.
    ```bash
    git status
    ```
2.  **Stage (Add):** Pick which files you want to save.
    ```bash
    # Add a specific file
    git add filename.txt

    # Add EVERYTHING in the folder
    git add .
    ```
3.  **Commit:** Save the files with a message.
    ```bash
    git commit -m "Added login feature"
    ```

---

## 3. Branching (Parallel Universes)
Never code on the main branch directly. Create a separate "timeline" for your code.

```bash
# Create a new branch
git branch feature-login

# Switch to that branch
git checkout feature-login

# SHORTCUT: Create AND Switch in one step (Most used)
git checkout -b feature-login

# Delete a branch (once you are done merging)
git branch -d feature-login
```

---

## 4. Undo & Fix Mistakes
Did you mess up? Here is how to go back.

**Level 1: I added a file but didn't commit yet.**
```bash
# Unstage the file (remove from the 'to-be-saved' list)
git restore --staged <filename>
```

**Level 2: I want to pause my work and switch branches.**
```bash
# Save changes to a temporary "backstage" area
git stash

# Bring the changes back when you are ready
git stash pop

# Throw away the stashed changes
git stash clear
```

**Level 3: I committed, but I want to go back in time.**
```bash
# 1. Get the commit ID (the long code next to your commit)
git log --oneline

# 2. Go back to that commit (keeps your file changes, just undoes the commit record)
git reset <commit_id>
```

---

## 5. Connecting to GitHub
Putting your code on the internet.

```bash
# Connect your local folder to a GitHub Repo
git remote add origin <your_repo_url>

# Verify the connection
git remote -v

# Push your code to the cloud (first time)
git push -u origin <branch_name>

# Push your code (subsequent times)
git push
```

---

## 6. Open Source / GSoC Workflow 🏆
How to contribute to big projects without breaking them.

**The Golden Rule:** Never push directly. Fork > Clone > Sync > Pull Request.

1.  **Fork:** Click the "Fork" button on the GitHub page of the project.
2.  **Clone:** Clone **your** fork (not the original).
    ```bash
    git clone <url_of_your_fork>
    ```
3.  **Link Upstream:** Connect to the original repo to get updates.
    ```bash
    git remote add upstream <url_of_original_company_repo>
    ```
4.  **Update:** Before coding, always download the latest changes from the original.
    ```bash
    git fetch upstream
    git merge upstream/main
    ```
5.  **Code & Push:** Create a branch, code, and push to **your** origin.
    ```bash
    git push origin my-feature-branch
    ```
6.  **PR:** Go to GitHub and click "New Pull Request".

---

## 7. Advanced: Clean History & Conflicts

### Squashing Commits
If you have 10 commits saying "typo", "fix", "wip", combine them into one clean commit.

```bash
# Interactively edit the last 3 commits
git rebase -i HEAD~3
```
*A text editor will open:*
1.  Leave the first word as `pick`.
2.  Change the other `pick` words to `squash` (or just `s`).
3.  Save and close. git will ask for one final message.

### Merge Conflicts
When two people edit the same line, Git panics.

1.  Open the file with the conflict.
2.  Look for these arrows:
    ```text
    <<<<<<< HEAD
    Code currently on your computer
    =======
    Code coming from GitHub
    >>>>>>> branch-name
    ```
3.  Delete the arrows and the code you **don't** want. Keep the correct code.
4.  Save the file.
5.  Run:
    ```bash
    git add .
    git commit -m "Fixed conflict"
    ```

---

## 8. Bonus: Ignoring Files (.gitignore)
You don't want to upload secret keys, huge video files, or system folders to GitHub.

1.  Create a file named `.gitignore`.
2.  Type the names of folders/files you want Git to ignore.
    ```text
    node_modules/
    .env
    .DS_Store
    secret_passwords.txt
    ```

---

## ✍️ Created By

**[Your Name Here]**
*   GitHub: [Link to your GitHub profile]
*   Email: [Your Email]
*   *Keep coding, keep committing!*
