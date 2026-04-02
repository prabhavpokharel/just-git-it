---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

---

# 01 — What is Git?

## The problem Git solves

Imagine you're writing an essay. You save it as:
```
essay.docx
essay_final.docx
essay_final_v2.docx
essay_ACTUALLY_final.docx
```

Now imagine doing that with 50 code files, on a team of 5 people.
That's chaos. Git solves this.

---

## What Git actually does

Git tracks **every change** you make to your files over time.

- What changed
- When it changed
- Who changed it
- Why it changed (via your message)

You can jump back to any previous state at any time.

---

## Key concepts (plain English)

| Term | What it means |
|------|--------------|
| **Repository (repo)** | Your project folder, tracked by Git |
| **Commit** | A saved snapshot of your project at a point in time |
| **Branch** | A parallel version of your project you can work on safely |
| **Remote** | A copy of your repo hosted online (e.g. GitHub) |
| **Clone** | Downloading a remote repo to your machine |
| **Push** | Uploading your commits to a remote repo |
| **Pull** | Downloading new commits from a remote repo |

---

## Where your code lives

```
Your Files (Working Directory)
        ↓  git add
Staging Area  ← "I want to include these changes in my next save"
        ↓  git commit
Local Repository  ← Saved on your machine
        ↓  git push
Remote Repository  ← Saved on GitHub (online, shareable)
```

This 4-step journey is the core of everything Git does.

---

## Git vs GitHub

| Git | GitHub |
|-----|--------|
| A tool you install on your computer | A website |
| Works completely offline | Requires internet |
| Tracks changes locally | Hosts your repos online |
| Free, open source | Free tier + paid plans |
| Created by Linus Torvalds (2005) | Owned by Microsoft |

> GitHub is not the only option. GitLab and Bitbucket do the same job.
> But GitHub is the most popular, so that's what we use here.

---

## ✅ You understand this section when you can answer:

1. What problem does Git solve?
2. What's the difference between a commit and a push?
3. What's the difference between Git and GitHub?

---

[🏠 Home](../README.md) · [02 — Setup →](../02-setup/README.md)

---
## 🧭 Navigation

| [🏠 Home](../README.md) | [01 — What is Git?](../01-what-is-git/README.md) | [02 — Setup](../02-setup/README.md) | [03 — Core Workflow](../03-core-workflow/README.md) | [04 — Branching](../04-branching/README.md) | [05 — Remote & GitHub](../05-remote-github/README.md) | [06 — Undoing Mistakes](../06-undoing-mistakes/README.md) | [07 — Collaboration](../07-collaboration/README.md) | [📋 Cheat Sheets](../cheatsheets/README.md) |
|---|---|---|---|---|---|---|---|---|

