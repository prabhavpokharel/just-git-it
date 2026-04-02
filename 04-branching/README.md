## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 04 — Branching

## Why branches exist

Without branches, everyone commits directly to the same code.
One bad commit breaks everything for everyone.

Branches let you work in **isolation**:
- Build a feature without affecting the main code
- Experiment freely — if it fails, just delete the branch
- Multiple people work on different things simultaneously

---

## The mental model

Think of your project as a timeline of commits:

```
main:  A ── B ── C ── D
```

When you create a branch, you get your own timeline that diverges:

```
main:     A ── B ── C ── D
                  \
feature:           E ── F ── G
```

`main` keeps working normally. You work on `feature`.
When `feature` is done and tested, you merge it back into `main`.

---

## Create a branch

```bash
git branch feature-login
```

This creates the branch but **doesn't switch to it**.

Create AND switch in one command (recommended):
```bash
git switch -c feature-login
```

---

## Switch between branches

```bash
git switch main          # go to main
git switch feature-login # go back to your feature branch
```

> Older command (still works, same thing):
> ```bash
> git checkout feature-login
> ```

---

## See all branches

```bash
git branch
```

Output:
```
* feature-login     ← the * shows which branch you're on
  main
```

---

## Work on your branch

Once you've switched, everything works exactly the same:

```bash
# You're on feature-login now
git add .
git commit -m "add login form HTML"

git add .
git commit -m "add login validation logic"
```

These commits exist **only on this branch**. `main` is untouched.

---

## Merge a branch into main

When your feature is done:

```bash
# Step 1: switch to main
git switch main

# Step 2: merge your feature branch in
git merge feature-login
```

Git combines the two timelines. Your feature's commits are now part of `main`.

---

## Merge conflicts

A conflict happens when the **same line** in the same file was changed differently on two branches.

Git can't decide which version to keep — so it asks you.

```
<<<<<<< HEAD (your current branch)
login button color: blue
=======
login button color: red
>>>>>>> feature-login (branch being merged)
```

To resolve:
1. Open the file
2. Delete the `<<<<`, `====`, `>>>>` markers
3. Keep whichever version (or combine them) — it's your call
4. Save the file
5. `git add .` and `git commit`

---

## Delete a branch (after merging)

Once merged, the branch is no longer needed:

```bash
git branch -d feature-login
```

Git will warn you if the branch hasn't been merged yet.
To force-delete anyway:
```bash
git branch -D feature-login
```

---

## Common branch naming conventions

| Pattern | Example | Used for |
|---------|---------|---------|
| `feature/` | `feature/user-login` | New features |
| `fix/` | `fix/null-pointer-error` | Bug fixes |
| `hotfix/` | `hotfix/payment-crash` | Urgent production fixes |
| `chore/` | `chore/update-dependencies` | Non-code maintenance |

---

## Quick reference

| Command | What it does |
|---------|-------------|
| `git branch` | List branches |
| `git branch <name>` | Create a branch |
| `git switch <name>` | Switch to a branch |
| `git switch -c <name>` | Create and switch |
| `git merge <name>` | Merge branch into current |
| `git branch -d <name>` | Delete a branch |

---

## ✅ Practice

1. Create a branch called `feature-about-page`
2. Switch to it, create a file, commit it
3. Switch back to `main` — notice the file is gone
4. Merge the branch into `main` — notice the file is back
5. Delete the branch

---

[← 03 — Core Workflow](../03-core-workflow/README.md) · [05 — Remote & GitHub →](../05-remote-github/README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

