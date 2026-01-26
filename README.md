# Git & GitHub Command Reference 🌻

> **Quick, practical Git commands to get things done.** No fluff, just the commands you'll actually use.

[![Last Updated](https://img.shields.io/badge/updated-January%202026-blue.svg)]()

---

## 📋 Table of Contents

- [Initial Setup](#-initial-setup)
- [Creating Repositories](#-creating-repositories)
- [Basic Workflow](#-basic-workflow)
- [Branching & Merging](#-branching--merging)
- [Remote Operations](#-remote-operations)
- [Undoing Changes](#-undoing-changes)
- [Checking Status & History](#-checking-status--history)
- [Stashing](#-stashing)
- [GitHub Specific](#-github-specific)
- [Useful Configurations](#-useful-configurations)
- [Common Workflows](#-common-workflows)

---

## ⚙️ Initial Setup

**First time Git setup:**
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global init.defaultBranch main
```

**Check your configuration:**
```bash
git config --list
git config user.name
```

---

## 📁 Creating Repositories

**Start a new project:**
```bash
git init
```

**Clone an existing repository:**
```bash
git clone <repository-url>
git clone <repository-url> <folder-name>
```

---

## 💾 Basic Workflow

**Check what changed:**
```bash
git status
```

**Stage files for commit:**
```bash
git add <file>              # Add specific file
git add .                   # Add all changes in current directory
git add -A                  # Add all changes in entire repository
git add *.js                # Add all .js files
```

**Commit changes:**
```bash
git commit -m "Your message here"
git commit -am "Message"    # Add and commit tracked files in one step
```

**Ignore files (create .gitignore):**
```bash
# Common .gitignore patterns:
node_modules/
.env
*.log
dist/
build/
.DS_Store
```

---

## 🌿 Branching & Merging

**Create and switch branches:**
```bash
git branch                     # List branches
git branch <branch-name>       # Create new branch
git checkout <branch-name>     # Switch to branch
git checkout -b <branch-name>  # Create and switch in one command
git switch <branch-name>       # Modern way to switch (Git 2.23+)
git switch -c <branch-name>    # Create and switch (modern)
```

**Merge branches:**
```bash
git merge <branch-name>        # Merge branch into current branch
```

**Delete branches:**
```bash
git branch -d <branch-name>    # Delete local branch (safe)
git branch -D <branch-name>    # Force delete local branch
git push origin --delete <branch-name>  # Delete remote branch
```

---

## 🌐 Remote Operations

**Connect to remote:**
```bash
git remote add origin <repository-url>
git remote -v                  # View remote connections
```

**Push to remote:**
```bash
git push origin <branch-name>
git push -u origin main        # Push and set upstream (first time)
git push                       # Push to tracked branch
```

**Pull from remote:**
```bash
git pull                       # Fetch and merge
git pull origin main
git fetch                      # Download changes without merging
```

**Update remote URL:**
```bash
git remote set-url origin <new-url>
```

---

## ↩️ Undoing Changes

**Discard changes in working directory:**
```bash
git restore <file>             # Discard changes (Git 2.23+)
git checkout -- <file>         # Old way to discard changes
```

**Unstage files:**
```bash
git restore --staged <file>    # Unstage (Git 2.23+)
git reset HEAD <file>          # Old way to unstage
```

**Undo commits:**
```bash
git reset --soft HEAD~1        # Undo last commit, keep changes staged
git reset --mixed HEAD~1       # Undo last commit, keep changes unstaged (default)
git reset --hard HEAD~1        # Undo last commit, discard changes (DANGEROUS!)
git revert <commit-hash>       # Create new commit that undoes changes (safe for shared branches)
```

**Amend last commit:**
```bash
git commit --amend -m "New message"      # Change last commit message
git commit --amend --no-edit             # Add changes to last commit without changing message
```

---

## 📊 Checking Status & History

**View commit history:**
```bash
git log
git log --oneline              # Compact view
git log --graph --oneline      # Visual branch graph
git log --all --graph --oneline --decorate  # Full visual history
git log -n 5                   # Last 5 commits
git log --author="Name"        # Filter by author
git log --since="2 weeks ago"  # Filter by date
```

**View changes:**
```bash
git diff                       # Unstaged changes
git diff --staged              # Staged changes
git diff <branch1> <branch2>   # Compare branches
git diff <commit1> <commit2>   # Compare commits
```

**Show specific commit:**
```bash
git show <commit-hash>
git show HEAD                  # Show last commit
```

---

## 📦 Stashing

**Temporarily save work:**
```bash
git stash                      # Stash changes
git stash save "Description"   # Stash with message
git stash list                 # View all stashes
git stash pop                  # Apply and remove last stash
git stash apply                # Apply last stash (keep it)
git stash apply stash@{0}      # Apply specific stash
git stash drop                 # Delete last stash
git stash clear                # Delete all stashes
```

---

## 🐙 GitHub Specific

**Create Pull Request (using GitHub CLI):**
```bash
gh pr create
gh pr list
gh pr checkout <number>
gh pr merge <number>
```

**Clone with SSH:**
```bash
git clone git@github.com:username/repository.git
```

**Fork workflow:**
```bash
# 1. Fork on GitHub, then clone your fork
git clone <your-fork-url>

# 2. Add original repo as upstream
git remote add upstream <original-repo-url>

# 3. Keep your fork updated
git fetch upstream
git merge upstream/main
```

**Create releases:**
```bash
git tag v1.0.0
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0
git push origin --tags         # Push all tags
```

---

## 🔧 Useful Configurations

**Helpful aliases:**
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm "commit -m"
git config --global alias.lg "log --oneline --graph --all"
```

**Set default editor:**
```bash
git config --global core.editor "code --wait"   # VS Code
git config --global core.editor "nano"          # Nano
```

**Enable color output:**
```bash
git config --global color.ui auto
```

---

## 🔄 Common Workflows

### **Starting a new project and pushing to GitHub:**
```bash
# 1. Create repository on GitHub first, then:
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <github-url>
git push -u origin main
```

### **Daily work on a feature:**
```bash
git checkout -b feature-name    # Create feature branch
# ... make changes ...
git add .
git commit -m "Add feature"
git push -u origin feature-name
# ... create PR on GitHub ...
```

### **Update your branch with latest main:**
```bash
git checkout main
git pull origin main
git checkout your-branch
git merge main
# ... resolve conflicts if any ...
```

### **Contributing to open source:**
```bash
# 1. Fork repository on GitHub
# 2. Clone your fork
git clone <your-fork-url>
cd <repository>

# 3. Add upstream remote
git remote add upstream <original-repo-url>

# 4. Create feature branch
git checkout -b fix-bug

# 5. Make changes and commit
git add .
git commit -m "Fix: description"

# 6. Push to your fork
git push origin fix-bug

# 7. Create Pull Request on GitHub
```

### **Emergency: Made changes on wrong branch:**
```bash
git stash                       # Save your changes
git checkout correct-branch     # Switch to right branch
git stash pop                   # Apply changes here
```

### **Syncing a fork:**
```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

---

## 🆘 Quick Troubleshooting

| Problem | Solution |
|:--------|:---------|
| **Merge conflict** | Edit files with `<<<<<<<` markers, then `git add <file>` and `git commit` |
| **Accidentally committed to wrong branch** | `git reset --soft HEAD~1`, `git stash`, switch branch, `git stash pop` |
| **Need to undo pushed commit** | `git revert <commit-hash>` then `git push` |
| **Forgot to add file to last commit** | `git add <file>` then `git commit --amend --no-edit` |
| **Can't push: rejected** | `git pull` first to sync, then `git push` |
| **Want to see what will be pushed** | `git diff origin/main..HEAD` |
| **Accidentally deleted branch** | `git reflog` to find commit, then `git checkout -b <branch> <commit-hash>` |

---

## 📚 Essential Resources

- **Documentation:** [git-scm.com/doc](https://git-scm.com/doc)
- **GitHub Guides:** [docs.github.com](https://docs.github.com)
- **Interactive Practice:** [learngitbranching.js.org](https://learngitbranching.js.org)
- **GitHub CLI:** [cli.github.com](https://cli.github.com)

---

## 💡 Pro Tips

1. **Commit often** — Small, focused commits are better than large ones
2. **Write clear commit messages** — Explain *why*, not just *what*
3. **Pull before you push** — Avoid conflicts by staying updated
4. **Never commit secrets** — Use `.gitignore` for API keys and passwords
5. **Branch for features** — Keep main branch stable
6. **Use `.gitignore` early** — Set it up before first commit

---

<div align="center">

**Found this helpful?** ⭐ Star this repo to bookmark it!

**Have suggestions?** Open an issue or submit a PR.

</div>