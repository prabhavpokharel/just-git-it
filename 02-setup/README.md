## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 02 — Setup

## Install Git

**macOS**
```bash
brew install git
```
> Don't have Homebrew? Install it at [brew.sh](https://brew.sh)

**Windows**
Download the installer from [git-scm.com](https://git-scm.com/download/win).
During install, choose **"Git Bash"** — use that as your terminal.

**Linux (Debian/Ubuntu)**
```bash
sudo apt install git-all
```

**Linux (Fedora/RHEL)**
```bash
sudo dnf install git-all
```

---

## Verify it worked

```bash
git --version
```

You should see something like `git version 2.43.0`.
If you get "command not found", installation didn't work — try again.

---

## Configure your identity

Git stamps every commit with your name and email.
Do this once — it applies to all your repos.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check it worked:
```bash
git config --list
```

---

## Set your default editor (optional but recommended)

When Git needs you to write a message, it opens a text editor.
The default is `vim`, which confuses beginners. Change it to VS Code:

```bash
git config --global core.editor "code --wait"
```

Or nano (simpler terminal editor):
```bash
git config --global core.editor "nano"
```

---

## Set up GitHub

1. Create a free account at [github.com](https://github.com)
2. Use the **same email** you configured above

### Connect Git to GitHub (SSH — recommended)

SSH lets Git talk to GitHub without asking for your password every time.

**Step 1: Generate an SSH key**
```bash
ssh-keygen -t ed25519 -C "you@example.com"
```
Press Enter through all prompts (defaults are fine).

**Step 2: Copy your public key**
```bash
cat ~/.ssh/id_ed25519.pub
```
Copy the entire output.

**Step 3: Add it to GitHub**
- Go to GitHub → Settings → SSH and GPG keys → New SSH key
- Paste your key → Save

**Step 4: Test it**
```bash
ssh -T git@github.com
```
You should see: `Hi username! You've successfully authenticated.`

---

## ✅ You're ready when:

- [ ] `git --version` returns a version number
- [ ] `git config --list` shows your name and email
- [ ] `ssh -T git@github.com` greets you by name

---

[← 01 — What is Git?](../01-what-is-git/README.md) · [03 — Core Workflow →](../03-core-workflow/README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

