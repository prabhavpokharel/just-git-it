## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 06 — Undoing Mistakes

Everyone makes mistakes. Git's entire point is that they're fixable.

Here's a decision tree — find your situation and use the right tool.

---

## Decision tree

```
Did you commit yet?
│
├── NO (changes are just in your working directory)
│   └── git restore <file>        ← throw away changes to a file
│   └── git restore .             ← throw away ALL unsaved changes
│
├── NO (changes are staged with git add, not committed yet)
│   └── git restore --staged <file>  ← unstage a file
│   └── git reset                    ← unstage everything
│
└── YES (already committed)
    │
    ├── Want to keep the history?
    │   └── git revert <hash>    ← create a new "undo" commit (SAFE)
    │
    └── Want to erase the history?
        └── git reset --hard <hash>  ← delete commits entirely (DANGEROUS)
```

---

## git restore — undo uncommitted changes

You edited a file and want to go back to the last committed version:

```bash
git restore index.html
```

Restore ALL files:
```bash
git restore .
```

> ⚠️ This is permanent. The changes are gone. Use carefully.

---

## git restore --staged — unstage a file

You ran `git add` but want to un-add it (without losing the changes):

```bash
git restore --staged index.html
```

The file stays modified in your working directory — it's just no longer staged.

---

## git stash — set work aside temporarily

You have changes you're not ready to commit, but need to switch branches.

```bash
git stash          # hide your current changes
git switch main    # go do other stuff
git switch feature-login
git stash pop      # bring your changes back
```

`stash pop` restores your changes AND removes them from the stash.

If you want to restore but keep a copy in the stash:
```bash
git stash apply    # restore but leave in stash too
```

View all stashes:
```bash
git stash list
```

---

## git revert — safely undo a commit

Creates a new commit that undoes the effects of a previous one.
The old commit stays in history. Safe for shared/public branches.

```bash
# First, find the commit hash
git log --oneline

# Then revert it
git revert a3f2c1b
```

Git opens an editor asking for a commit message.
Save and close it. Done — a new "Revert" commit is added.

**When to use:** You've already pushed the commit and others might have it.

---

## git reset — move back to a previous commit

Moves your branch pointer back in history. Commits after the target are removed.

```bash
git reset --hard a3f2c1b
```

**`--hard`**: Deletes the commits AND discards all the changes in those commits. Gone forever.

```bash
git reset --soft a3f2c1b
```

**`--soft`**: Removes the commits but keeps all the changes as staged. Useful if you want to re-commit differently.

> ⚠️ **Don't use `git reset` on commits you've already pushed** — it rewrites history and breaks things for teammates. Use `git revert` instead.

---

## git push --force — after a reset (danger zone)

If you reset locally and need to push:

```bash
git push --force origin main
```

This overwrites the remote with your local version.

> ⚠️ Only do this if you're the only person on the branch, or you've told your team.
> This deletes history from the remote. It cannot be undone.

---

## Side-by-side comparison

| Situation | Command | Safe to use on shared branches? |
|-----------|---------|--------------------------------|
| Undo unsaved file changes | `git restore <file>` | ✅ Yes |
| Unstage a file | `git restore --staged <file>` | ✅ Yes |
| Hide changes temporarily | `git stash` | ✅ Yes |
| Undo a pushed commit (safely) | `git revert <hash>` | ✅ Yes |
| Delete commits from history | `git reset --hard <hash>` | ❌ No |
| Force push after reset | `git push --force` | ❌ No |

---

## Quick reference

| Command | What it does |
|---------|-------------|
| `git restore <file>` | Discard changes to a file |
| `git restore .` | Discard ALL uncommitted changes |
| `git restore --staged <file>` | Unstage a file |
| `git stash` | Stash changes temporarily |
| `git stash pop` | Restore stashed changes |
| `git stash list` | See all stashes |
| `git revert <hash>` | Undo a commit safely (adds new commit) |
| `git reset --soft <hash>` | Remove commits, keep changes staged |
| `git reset --hard <hash>` | Remove commits AND changes |
| `git push --force` | Overwrite remote (dangerous) |

---

## ✅ Practice

1. Edit a file, then use `git restore` to undo it
2. Stage a file, then unstage it with `git restore --staged`
3. Make a commit you want to undo, use `git revert` to reverse it
4. Use `git stash` to hide changes, switch branches, come back, and pop them

---

[← 05 — Remote & GitHub](../05-remote-github/README.md) · [07 — Collaboration →](../07-collaboration/README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

