## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 📋 Cheat Sheets

Quick reference for everything in this guide. Bookmark this page.

---

## Master Git Cheat Sheet

### Setup
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --list                          # verify config
```

### Starting a repo
```bash
git init                                   # new local repo
git clone <url>                            # copy remote repo locally
```

### Core daily workflow
```bash
git status                                 # what's changed?
git add <file>                             # stage a file
git add .                                  # stage all changes
git commit -m "message"                    # save a snapshot
git log --oneline                          # see history
```

### Branches
```bash
git branch                                 # list branches
git branch <name>                          # create branch
git switch <name>                          # switch to branch
git switch -c <name>                       # create + switch
git merge <name>                           # merge into current branch
git branch -d <name>                       # delete (safe)
git branch -D <name>                       # delete (force)
```

### Remote (GitHub)
```bash
git remote add origin <url>               # connect to GitHub
git remote -v                              # show remotes
git push origin <branch>                  # upload commits
git push -u origin <branch>               # upload + set default
git pull origin <branch>                  # download + merge
git fetch                                  # download (don't merge)
```

### Undoing things
```bash
git restore <file>                         # discard file changes
git restore .                              # discard ALL changes
git restore --staged <file>               # unstage a file
git stash                                  # hide changes temporarily
git stash pop                              # restore hidden changes
git stash list                             # see all stashes
git revert <hash>                          # undo a commit (safe)
git reset --soft <hash>                    # remove commits, keep changes
git reset --hard <hash>                    # remove commits + changes
git push --force                           # overwrite remote (danger!)
```

### Inspecting
```bash
git log                                    # full commit history
git log --oneline                          # compact history
git log --oneline --graph                 # visual branch graph
git diff                                   # changes not yet staged
git diff --staged                          # changes that are staged
git diff <hash1> <hash2>                  # compare two commits
git show <hash>                            # see what a commit changed
```

---

## Commit message cheat sheet

```
Format:
  <type>: <short description>

Types:
  feat:     new feature
  fix:      bug fix
  docs:     documentation only
  style:    formatting, no logic change
  refactor: code change, no feature/fix
  test:     adding tests
  chore:    maintenance, dependencies

Examples:
  feat: add user login with JWT
  fix: prevent crash when email is null
  docs: update README with setup steps
  chore: upgrade dependencies to latest
```

---

## .gitignore patterns cheat sheet

```gitignore
# Ignore a specific file
secrets.txt

# Ignore all .log files
*.log

# Ignore a folder and everything in it
node_modules/
dist/
.next/
__pycache__/

# Ignore a file in any subfolder
**/.DS_Store

# Ignore everything in a folder except one file
logs/*
!logs/.gitkeep

# Common ignores by language
# JavaScript/Node
node_modules/
.env
.env.local
dist/
build/

# Python
__pycache__/
*.pyc
.venv/
*.egg-info/

# macOS
.DS_Store

# Windows
Thumbs.db
```

---

## Workflow cheat sheet

### Solo project
```
git init → work → git add . → git commit -m "" → git push
```

### Team feature branch
```
git pull origin main
git switch -c feature/my-feature
  → work, add, commit (repeat)
git push -u origin feature/my-feature
  → open PR on GitHub
  → get review → merge
git switch main && git pull origin main
git branch -d feature/my-feature
```

### Something went wrong
```
Not committed:    git restore <file>
Staged:           git restore --staged <file>
Committed:        git revert <hash>
Need to switch:   git stash → switch → git stash pop
```

---

[← 07 — Collaboration](../07-collaboration/README.md) · [🏠 Back to Home](../README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

