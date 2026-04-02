---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 05 — Remote & GitHub

So far everything has been local — on your machine only.
This section connects your work to GitHub.

---

## Two ways to start

### Option A: You have a local project → put it on GitHub

```bash
# 1. On GitHub: create a new empty repo (don't add README)
# 2. Copy the SSH URL (looks like: git@github.com:username/repo-name.git)

# 3. In your terminal, inside your project:
git remote add origin git@github.com:username/repo-name.git

# 4. Push your code up
git push -u origin main
```

Done. Your code is now on GitHub.

---

### Option B: Repo exists on GitHub → get it on your machine

```bash
git clone git@github.com:username/repo-name.git
```

This downloads the repo, creates a folder, and sets up the remote automatically.

---

## Understanding "origin"

`origin` is just a nickname for your remote repo's URL.

When you run `git remote add origin <url>`, you're saying:
> "Whenever I say `origin`, I mean this URL."

You can see your remotes:
```bash
git remote -v
```

Output:
```
origin  git@github.com:username/repo-name.git (fetch)
origin  git@github.com:username/repo-name.git (push)
```

---

## Push — send your commits to GitHub

```bash
git push origin main
```

Sends all your local commits on `main` to GitHub.

The first time you push a new branch, use `-u` to set the upstream:
```bash
git push -u origin main
```

After that, `git push` alone is enough (it remembers).

---

## Pull — get new commits from GitHub

Someone else pushed changes. Or you made changes on GitHub directly.
Pull brings them to your machine:

```bash
git pull origin main
```

`git pull` = `git fetch` + `git merge` in one command.

---

## Fetch vs Pull

| Command | What it does |
|---------|-------------|
| `git fetch` | Downloads new commits but doesn't apply them |
| `git pull` | Downloads AND applies (merges) them |

Use `git fetch` when you want to see what changed before applying it.
Use `git pull` when you just want to stay up to date.

---

## Pushing a branch to GitHub

```bash
# You're on feature-login branch
git push -u origin feature-login
```

This creates the branch on GitHub too.

---

## Full remote workflow (team scenario)

```bash
# 1. Get the latest main before starting work
git switch main
git pull origin main

# 2. Create a feature branch
git switch -c feature-user-profile

# 3. Do your work, commit as you go
git add .
git commit -m "add user profile page"

# 4. Push your branch to GitHub
git push -u origin feature-user-profile

# 5. On GitHub: open a Pull Request (see section 07)
```

---

## Common errors and fixes

### "rejected — non-fast-forward"
```
! [rejected] main -> main (non-fast-forward)
```
Someone else pushed before you. Fix:
```bash
git pull origin main   # get their changes first
git push origin main   # now push yours
```

### "Permission denied (publickey)"
Your SSH key isn't set up correctly.
Go back to [02 — Setup](../02-setup/README.md) and redo the SSH section.

### "remote origin already exists"
```bash
git remote remove origin
git remote add origin <your-url>
```

---

## Quick reference

| Command | What it does |
|---------|-------------|
| `git remote add origin <url>` | Connect local repo to GitHub |
| `git remote -v` | Show remote URLs |
| `git clone <url>` | Download a repo from GitHub |
| `git push origin <branch>` | Upload commits to GitHub |
| `git push -u origin <branch>` | Upload + set default upstream |
| `git pull origin <branch>` | Download + merge from GitHub |
| `git fetch` | Download without merging |

---

## ✅ Practice

1. Create a new empty repo on GitHub
2. Connect your local project from section 03 to it
3. Push your commits
4. Make a change on GitHub directly (edit a file in the browser)
5. Pull that change down to your machine

---

[← 04 — Branching](../04-branching/README.md) · [06 — Undoing Mistakes →](../06-undoing-mistakes/README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

