# Git Command List

This document provides a concise list of essential Git commands for initial configuration, branch management, and commit operations. Each command includes a brief explanation to help you understand its purpose and usage.

---

## Initial Configuration

Set up your Git environment with your user information and preferred settings:

```sh
git config --global user.name "John Doe"           # Set your name for commits
git config --global user.email johndoe@example.com  # Set your email for commits
git config --global init.defaultBranch main         # Set default branch name to 'main'
git config --global core.editor "code --wait"      # Use VS Code as default editor
git config --global -e                             # Edit global config file manually
```

Configure line endings based on your operating system:

```sh
git config --global core.autocrlf true   # Use on Windows
git config --global core.autocrlf input  # Use on Mac/Linux
```

---

## Branch Management

Clone a repository:

```sh
git clone <repository-url>
```

List all branches:

```sh
git branch
```

Create a new branch:

```sh
git branch dev
```

Switch to a branch:

```sh
git checkout dev
```

---

## Commit Workflow

Check the status of your working directory:

```sh
git status
```

Stage all changes:

```sh
git add .
```

Commit staged changes with a message:

```sh
git commit -m "Commit description"
```

Push your branch to the remote repository:

```sh
git push origin dev
```

---

## Useful Git Commands

### Stashing Changes

Temporarily save changes that are not ready to commit:

```sh
git stash                # Stash current changes
git stash list           # List all stashes
git stash apply          # Reapply the most recent stash
git stash pop            # Apply and remove the most recent stash
```

### Merging and Rebasing

Integrate changes from another branch:

```sh
git merge <branch>       # Merge specified branch into current branch
git rebase <branch>      # Rebase current branch onto specified branch
```

### Viewing History

See commit history and changes:

```sh
git log                  # Show commit history
git log --oneline        # Compact commit history
git log --graph --all    # Visualize branch history
git diff                 # Show unstaged changes
git diff --staged        # Show staged changes
```

### Undoing Changes

Undo or reset changes:

```sh
git checkout -- <file>   # Discard changes in working directory
git reset HEAD <file>    # Unstage a file
git revert <commit>      # Create a new commit that undoes a previous commit
git reset --hard <commit># Reset to a specific commit (dangerous)
```

### Working with Tags

Create and manage tags:

```sh
git tag                  # List tags
git tag <tagname>        # Create a new tag
git tag -d <tagname>     # Delete a tag
git push origin <tagname># Push a tag to remote
```

### Working with Remotes

Manage remote repositories:

```sh
git remote -v            # List remote repositories
git remote add origin <url> # Add a new remote
git fetch origin         # Fetch changes from remote
git pull origin <branch> # Pull changes from remote branch
git push origin <branch> # Push changes to remote branch
```

---

## Removing Files by Name or Extension from Git Index and Locally

This section explains how to remove files by filename or extension from the Git index (without deleting them locally) and how to delete them from your local filesystem. Replace `<pattern>` with your desired filename or extension (e.g., `*.log`, `*.tmp`, `filename.txt`).

### 1. Remove from Git Index (without deleting locally)

#### Windows (PowerShell):

```powershell
Get-ChildItem -Path . -Recurse -Filter <pattern> | ForEach-Object { git rm --cached $_.FullName }
```

#### Linux/Mac (Bash):

```bash
find . -type f -name "<pattern>" -exec git rm --cached {} +
```

### 2. Delete Files Locally

#### Windows (PowerShell):

```powershell
Get-ChildItem -Path . -Recurse -Filter <pattern> | Remove-Item
```

#### Linux/Mac (Bash):

```bash
find . -type f -name "<pattern>" -delete
```

---

## Example of removing `.min.*` Files from Git Index and Locally

This section explains how to remove all `.min.*` files from the Git index (without deleting them locally) and how to delete them from your local filesystem. Commands are provided for Windows (PowerShell), Linux, and Mac.

### 1. Remove from Git Index (without deleting locally)

#### Windows (PowerShell):

```powershell
Get-ChildItem -Path . -Recurse -Filter *.min.* | ForEach-Object { git rm --cached $_.FullName }
```

#### Linux/Mac (Bash):

```bash
find . -type f -name "*.min.*" -exec git rm --cached {} +
```

### 2. Delete Files Locally

#### Windows (PowerShell):

```powershell
Get-ChildItem -Path . -Recurse -Filter *.min.* | Remove-Item
```

#### Linux/Mac (Bash):

```bash
find . -type f -name "*.min.*" -delete
```

---

## Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Git Branching Guide](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
