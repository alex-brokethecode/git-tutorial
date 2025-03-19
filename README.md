# Git Tutorial

# Git commands

```shell
# Initial configure
git config --global user.name <username>
git config --global user.email <email>

# Set default branch
git config --global init.defaultBranch <branch>

# Remove a configuration
git config --global --unset <setting>

# See configuration
git config --global --list
git config --local --list

# Basic commands
git init
git add <file>
git commit -m <message>

# Check history
git log

# Move between commits (HEAD)
git checkout <hash>
git checkout <branch> # Back to last commit
git checkout -f <branch> # Force back to last commit

# Remote repository
git branch -M <branch> # Change branch to main
git remote add origin <link> # Set remote repository
git remote add <name> <link> # Set more than 1 repository
git push -u origin main # Push to remote repository

# ---

# Branch
git branch <name> # Create branch
git checkout <branch> # Move to branch
git checkout -b <name> # Create and move to branch
git branch <name> <source-branch> # Create branch based on a specific branch

# Remote branch
git push --set-upstream origin <branch> # Sync local branch in remote repository
git push -u origin <branch> # Sync local branch to remote
git pull origin <branch> # Get changes from specific branch
git pull # Shortcut to pull changes from origin in the current branch

# Merge
git merge <branch> # Merge changes "from" branch into the current branch

# Reset
git reset <hash> # Move to commit and move last commits changes in working directory (untracking)
git reset --soft <hash> # Move to commit and keep last commits changes in stagging
git reset --hard <hash> # Move to commit and delete all last commits changes

git revert # Move to past commit but keeping previous commits

# Stash
git stash # Create a temporary copy of your changes
git stash list # List saved stashes
git stash apply <name> # Get changes from a specific stash
```

## Commit format

> [!INFO] Recommendations
>
> - Your commits should answer this: "If applied to the codebase, this commit will ..." / "What will happen when I merge the branch containing this commit?"
> - e.g. Upgrade the package by ..., fix thread allocation by ... (imperative)

## Pull Request

- Create a PR in your remote repository
- Select from which branch to another branch
- Select create
- Select merge
- Additionally, you can delete the old branch

## Common Workflow

> [!INFO] Steps
>
> 1. Clone the repository
> 2. Create a new branch from the `main` or another branch
> 3. Make your changes
> 4. Push the branch to the remote repo
> 5. Open Pull Request
> 6. Merge the changes
> 7. Pull the merged changes into your local `main` branch
> 8. Repeat from step 2

---

# Another commands

```bash
# Revert file changes
git restore <file>
git checkout <file>

# Alias
git config --global alias.tree "log --graph"

# Diff
git diff # See changes
```

## .gitignore

```text
**/venv
```
