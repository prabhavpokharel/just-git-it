---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 07 — Collaboration

This is how real teams use Git day-to-day.

---

## The standard team workflow

```
1. Pull latest main
2. Create a feature branch
3. Do your work, commit often
4. Push your branch to GitHub
5. Open a Pull Request (PR)
6. Team reviews your code
7. Merge into main
8. Delete the branch
```

This is called a **feature branch workflow**. Most teams use some version of it.

---

## Pull Requests (PRs)

A Pull Request is a request to merge your branch into another branch (usually `main`).

It's not a Git feature — it's a GitHub feature. It lives on the website.

### Why PRs exist

- Someone else reviews your code before it goes into `main`
- Catches bugs and bad patterns before they ship
- Creates a record of what changed and why
- Everyone on the team can see what's being worked on

### How to open a PR

1. Push your branch to GitHub
   ```bash
   git push -u origin feature-login
   ```

2. Go to your repo on GitHub

3. GitHub will show a banner: **"feature-login had recent pushes — Compare & pull request"**
   Click it.

4. Fill in:
   - **Title**: short summary of what you did
   - **Description**: what changed, why, anything reviewers should know

5. Click **"Create pull request"**

---

## Reviewing a PR

When someone asks you to review:

1. Open the PR on GitHub
2. Click **"Files changed"** tab
3. Read the diff (green = added, red = removed)
4. Leave comments on specific lines by clicking the `+` icon
5. When done: **Approve**, **Request changes**, or just **Comment**

### Good review comments

| ❌ Unhelpful | ✅ Helpful |
|------------|-----------|
| "This is wrong" | "This will fail if `user` is null — add a null check on line 12" |
| "I don't like this" | "Consider using `map()` here instead of the for-loop — it's more readable" |
| "fix it" | "The variable name `x` isn't clear — maybe `userCount`?" |

---

## Merging a PR

Once approved:

1. Click **"Merge pull request"**
2. Click **"Confirm merge"**
3. Click **"Delete branch"** (keep things tidy)

Back on your machine:
```bash
git switch main
git pull origin main    # get the merged changes
git branch -d feature-login  # delete local branch too
```

---

## Keeping your branch up to date

While you work on your branch, `main` moves forward.
Before merging, bring those updates into your branch.

**Option 1 — Merge main into your branch** (simple, recommended for beginners)
```bash
git switch feature-login
git merge main
```

**Option 2 — Rebase onto main** (cleaner history, more advanced)
```bash
git switch feature-login
git rebase main
```

Rebase rewrites your commits as if you'd started from the latest `main`.
Result: a perfectly linear history. But it rewrites commit IDs — don't rebase branches others are using.

---

## Forking (contributing to someone else's project)

You can't push directly to a repo you don't own.
Instead:

1. **Fork** the repo (GitHub button, top right) — creates your own copy on GitHub
2. **Clone** your fork locally
3. Create a branch, make changes, push to your fork
4. Open a PR from your fork into the original repo

This is how all open-source contributions work.

---

## .github folder (optional but common)

Many repos have a `.github/` folder with templates:

```
.github/
  PULL_REQUEST_TEMPLATE.md    ← pre-fills PR descriptions
  ISSUE_TEMPLATE.md           ← pre-fills bug reports
  workflows/                  ← GitHub Actions (automation)
```

---

## Common team rules

Most teams enforce these on `main`:

- **No direct pushes to `main`** — everything goes through a PR
- **At least 1 approval** required before merging
- **All tests must pass** before merging
- **Delete branches after merging**

---

## Quick reference

| Action | How |
|--------|-----|
| Open a PR | Push branch → GitHub → "Compare & pull request" |
| Review a PR | Files changed tab → leave comments |
| Merge a PR | GitHub "Merge pull request" button |
| Update branch with main | `git merge main` or `git rebase main` |
| Fork a repo | GitHub "Fork" button |
| Contribute to open source | Fork → branch → PR |

---

## ✅ Practice

1. Pair with someone (or use two GitHub accounts)
2. One person creates a repo, adds the other as a collaborator
3. Each person creates a branch and makes changes
4. Both open PRs, review each other's code, leave comments
5. Merge both PRs

---

## 🎉 You've finished the main guide!

You now know:
- ✅ What Git is and how it works
- ✅ How to set up Git and GitHub
- ✅ The core add → commit → push workflow
- ✅ How to work with branches
- ✅ How to undo mistakes safely
- ✅ How to collaborate with pull requests

**Keep these handy →** [Cheat Sheets](../cheatsheets/README.md)

---

[← 06 — Undoing Mistakes](../06-undoing-mistakes/README.md) · [📋 Cheat Sheets →](../cheatsheets/README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

