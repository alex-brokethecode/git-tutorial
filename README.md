# Git Tutorial

## 🔹 Git Configuration

```shell
# Set global username and email
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Set default branch name
git config --global init.defaultBranch main

# Remove a specific configuration
git config --global --unset <setting>

# View configuration settings
git config --global --list
```

## 🔹 Basic Commands

```shell
# Initialize a new Git repository
git init

# Stage files for commit
git add <file>

# Commit staged changes with a message
git commit -m "Your commit message"
```

## 🔹 Checking History & Moving Between Commits

```shell
# View commit history
git log

# Checkout a specific commit
git checkout <commit-hash>

# Switch to another branch
git checkout <branch>

# Force reset to last commit
git checkout -f <branch>
```

## 🔹 Working with Remote Repositories

```shell
# Set up remote repository
git remote add origin <repository-url>

# Push changes to remote repository
git push -u origin main

# Add upstream repository (for forks)
git remote add upstream <repository-url>
```

## 🔹 Branching

```shell
# Create a new branch
git branch <branch-name>

# Switch to an existing branch
git checkout <branch>

git checkout -b <branch-name> # Create and switch to a new branch

git branch -d <branch-name> # Delete a branch

# Alternative way to switch branches
git switch <branch>
git switch -c <branch-name> # Create and switch
```

## 🔹 Synchronizing with Remote Branch

```shell
# Push branch to remote repository
git push --set-upstream origin <branch>

# Pull latest changes from a branch
git pull origin <branch>

git fetch # Fetch updates without merging
```

## 🔹 Merging & Rebasing

```shell
# Merge another branch into the current branch
git merge <branch>

# Rebase (integrates commits more cleanly)
git rebase <branch>
```

> **📝 Merge vs. Rebase:**
>
> - `git merge` creates a new merge commit.
> - `git rebase` moves your commits on top of the latest remote branch, keeping history cleaner.

## 🔹 Reset & Revert

```shell
# Reset to a previous commit (unstage changes)
git reset <commit-hash>

# Keep staged changes but move HEAD
git reset --soft <commit-hash>

# Reset completely (delete changes)
git reset --hard <commit-hash>

# Create a new commit that undoes a previous commit
git revert <commit-hash>
```

## 🔹 Stashing

```shell
# Save changes temporarily
git stash

# List saved stashes
git stash list

# Apply last saved stash
git stash pop

# Apply a specific stash
git stash apply stash@{index}

# Remove a stash
git stash drop
```

## 🔹 Commit Message Guidelines

> - ✅ Use imperative tone: "Fix bug", "Add feature" instead of "Fixed bug".
> - ✅ Keep messages concise and meaningful.
> - ✅ Each commit should be self-contained.

## 🔹 Pull Requests (PRs)

1. Create a branch for your feature or fix.
2. Push the branch to the remote repository.
3. Open a Pull Request.
4. Select the target branch (e.g., `main`).
5. Merge the changes.
6. Optionally, delete the branch.

## 🔹 Common Git Workflow

```shell
# Clone a repository
git clone <repository-url>

# Create and switch to a new branch
git checkout -b feature-branch

# Work on changes, then stage and commit
git add .
git commit -m "Add feature"

# Push to remote repository
git push -u origin feature-branch

# Create a Pull Request & Merge

# Update local main branch after merge
git checkout main
git pull origin main

# Delete local branch after merge
git branch -d feature-branch
```

## 🔹 Other Useful Commands

```shell
# Restore a file to last committed state
git restore <file>

# Show differences between working directory and last commit
git diff

# View commit history in tree format
git log --graph --oneline --decorate

# View all previous commits (even after reset)
git reflog
```

## 🔹 Git Ignore (`.gitignore`)

```text
# Ignore virtual environments, logs, and system files
**/venv
*.log
.DS_Store
node_modules/
```

## Git Flow

**Git Flow** is a branching model for Git that defines a strict workflow for managing features, releases, and hotfixes.

### 🔹 Branches in Git Flow

- `main` → Always stable, used for production.
- `develop` → Integration branch for ongoing development.
- `feature/*` → Created from `develop` for new features.
- `release/*` → Created from `develop` to prepare for a new release.
- `hotfix/*` → Created from `main` to fix critical issues.

### 🔄 Workflow Steps

1. Create a `feature/*` branch from `develop`.
2. Work on the feature, commit, and push changes.
3. Merge `feature/*` into `develop` once complete.
4. When ready to release, create a `release/*` branch from `develop`.
5. Test and stabilize the release, then merge it into `main` and `develop`.
6. If a critical bug is found, create a `hotfix/*` from `main`, fix it, and merge it back into `main` and `develop`.

## GitHub Flow

**GitHub Flow** is a simpler, more lightweight workflow designed for continuous deployment and collaboration.

### 🔄 Workflow Steps

1. Create a new branch from `main` for each feature or fix.
2. Work on the branch, commit, and push changes.
3. Open a **Pull Request (PR)** for code review.
4. After approval, merge the PR into `main`.
5. Deploy immediately after merging.

| Feature              | Git Flow                   | GitHub Flow                |
| -------------------- | -------------------------- | -------------------------- |
| **Complexity**       | High                       | Low                        |
| **Best for**         | Large projects             | Fast-paced development     |
| **Main Branches**    | `main`, `develop`          | `main` only                |
| **Feature Branches** | `feature/*`                | Short-lived branches       |
| **Releases**         | Managed via `release/*`    | Directly from `main`       |
| **Hotfixes**         | `hotfix/*` from `main`     | Direct fix in a new branch |
| **Deployment**       | After a structured release | Continuous Deployment      |
