## 1. Create & Switch Branch

```bash
# List branches
git branch

# List all branches (local + remote)
git branch -a

# Create new branch
git branch feature

# Switch branch
git switch feature

# Create and switch to new branch
git switch -c feature

# Rename current branch
git branch -m new-name
```

## 2. Delete Branch

```bash
# Delete local branch (safe)
git branch -d feature

# Force delete local branch
git branch -D feature

# Delete remote branch
git push origin --delete feature
```

## 3. Merge Branch

```bash
# Merge feature into current branch
git merge feature

# Force merge commit (disable fast-forward)
git merge --no-ff feature

# Squash merge
git merge --squash feature

# Abort merge
git merge --abort
```

## 4. Rebase Branch
```bash
# Rebase current branch onto main
git rebase main

# Continue after resolving conflicts
git rebase --continue

# Abort rebase
git rebase --abort
```

## 5. Remote Branch

```bash
# Fetch latest remote branches
git fetch

# Push new branch to remote
git push -u origin feature

# Track remote branch
git switch --track origin/feature

# Update current branch
git pull

# Remove stale remote-tracking branches
git fetch --prune
```


## 6. Useful Branch Commands

```bash
# Show current branch
git branch --show-current

# Show merged branches
git branch --merged

# Show unmerged branches
git branch --no-merged

# Show branch commit history
git log --oneline --graph --all
```

## Quick Reference

| Command                      | Purpose                 |
| ---------------------------- | ----------------------- |
| `git switch -c feature`      | Create + switch         |
| `git switch main`            | Switch branch           |
| `git branch -d feature`      | Delete branch           |
| `git merge feature`          | Merge branch            |
| `git merge --no-ff feature`  | Force merge commit      |
| `git merge --squash feature` | Squash merge            |
| `git rebase main`            | Rebase onto main        |
| `git fetch`                  | Download remote updates |
| `git push -u origin feature` | Push + set upstream     |
| `git branch -a`              | List all branches       |