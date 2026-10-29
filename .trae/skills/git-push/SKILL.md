---
name: "git-push"
description: "Commits and pushes the current project to GitHub (https://github.com/seagullLMH/Lvmohan.git). Invoke when user asks to commit, push, upload, or submit the project to GitHub."
---

# Git Push to GitHub

This skill commits all current project files and pushes them to the remote GitHub repository.

## Remote Repository

- **URL**: `https://github.com/seagullLMH/Lvmohan.git`
- **Access**: SSH public key has been configured for this repository

## Steps

1. Check if `.git` directory exists in the project root. If not, run:
   ```
   git init
   ```

2. Check if remote `origin` is already set. If not, run:
   ```
   git remote add origin https://github.com/seagullLMH/Lvmohan.git
   ```
   If it exists but points to a different URL, update it:
   ```
   git remote set-url origin https://github.com/seagullLMH/Lvmohan.git
   ```

3. Add all files (including new and modified):
   ```
   git add .
   ```

4. Commit with a descriptive message. Use current date/time and a summary of changes:
   ```
   git commit -m "feat: update project [YYYY-MM-DD]"
   ```

5. Check current branch name (`git branch --show-current`). If empty (detached HEAD state), create `main`:
   ```
   git checkout -b main
   ```

6. Push to remote with upstream tracking:
   ```
   git push -u origin main
   ```
   If the branch is not `main`, push using the actual branch name.

## Notes

- On first push, Git may ask for username/password or passphrase. Follow the prompts.
- If `main` branch does not exist remotely yet, `-u` sets the tracking relationship automatically.
- If there are merge conflicts with remote changes, inform the user before resolving.
- After successful push, report the commit hash and message to the user.
