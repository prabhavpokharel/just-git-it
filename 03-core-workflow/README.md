---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 03 — Core Workflow

This is the loop you'll repeat dozens of times every day.
Learn this cold.

```
make changes → git add → git commit → repeat
```

---

## Start a new project

```bash
mkdir my-project    # create a folder
cd my-project       # go into it
git init            # tell Git to track this folder
```

`git init` creates a hidden `.git` folder inside your project.
That folder IS the repository — don't delete it.

---

## Check what's going on at any time

```bash
git status
```

Run this constantly. It tells you:
- Which files have changed
- Which changes are staged (ready to commit)
- Which changes are not staged yet

> **`git status` is your best friend.** When in doubt, run it.

---

## Stage your changes — `git add`

Staging means: "I want to include this in my next commit."

```bash
# Stage a specific file
git add filename.txt

# Stage all changes in current folder
git add .

# Stage everything in the whole project
git add --all
```

### The staging area explained

You don't have to commit everything at once.
Staging lets you pick exactly what goes into each commit.

```
Changed files:          Staged:
  login.py       →  git add login.py  →  login.py  ✓
  styles.css     →  (not staged yet)  →  (not included)
```

This means your commit can say "fix login bug" and only contain login-related files — even if you were also editing CSS.

---

## Commit your changes — `git commit`

A commit is a permanent snapshot with a message explaining what you did.

```bash
git commit -m "your message here"
```

### Writing good commit messages

| ❌ Bad | ✅ Good |
|--------|---------|
| `fix stuff` | `fix null pointer error in user login` |
| `changes` | `add password validation to signup form` |
| `asdfgh` | `remove unused CSS from homepage` |
| `update` | `update README with installation steps` |

**Rule:** Future-you should be able to read the message and know exactly what changed, without opening the file.

---

## See your commit history — `git log`

```bash
git log
```

Shows every commit: hash, author, date, message.

For a cleaner view:
```bash
git log --oneline
```

Output looks like:
```
a3f2c1b fix login validation bug
9d4e8a2 add user profile page
1bc7f30 initial commit
```

That 7-character code (e.g. `a3f2c1b`) is the **commit hash** — a unique ID for that snapshot. You'll use these when undoing mistakes.

---

## Full example walkthrough

```bash
# 1. Create a project
mkdir my-app && cd my-app
git init

# 2. Create a file
echo "Hello, world" > index.txt

# 3. Check status — Git sees an untracked file
git status

# 4. Stage it
git add index.txt

# 5. Commit it
git commit -m "add index.txt with hello world"

# 6. Make a change
echo "Second line" >> index.txt

# 7. Stage and commit
git add .
git commit -m "add second line to index.txt"

# 8. See the history
git log --oneline
```

---

## .gitignore — files Git should ignore

Some files should never be committed: passwords, API keys, dependencies, build output.

Create a file called `.gitignore` in your project root:

```
# Example .gitignore

node_modules/       # JavaScript dependencies (huge, auto-generated)
.env                # Environment variables (often contains secrets)
*.log               # Log files
.DS_Store           # macOS system file
__pycache__/        # Python cache
dist/               # Build output
```

Any file or folder listed here will be completely invisible to Git.

> ⚠️ **Never commit passwords, API keys, or secrets.** Once pushed to GitHub, they're public. Use `.gitignore` and `.env` files.

---

## Quick reference

| Command | What it does |
|---------|-------------|
| `git init` | Start tracking a folder |
| `git status` | See what's changed |
| `git add .` | Stage all changes |
| `git add <file>` | Stage one file |
| `git commit -m "msg"` | Save a snapshot |
| `git log --oneline` | See commit history |

---

## ✅ Practice this before moving on

1. Create a new folder and run `git init`
2. Create 2 files, add content to them
3. Stage and commit them separately with meaningful messages
4. Edit one file, stage only that one, commit it
5. Run `git log --oneline` and read the history

---

[← 02 — Setup](../02-setup/README.md) · [04 — Branching →](../04-branching/README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

