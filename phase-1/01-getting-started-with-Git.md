<div align="center">
 
# 📗 01 — Getting Started with Git
 
![Phase](https://img.shields.io/badge/Phase-1-blue?style=flat-square)
![Topic](https://img.shields.io/badge/Topic-Fundamentals-green?style=flat-square)
![Level](https://img.shields.io/badge/Level-Beginner-yellow?style=flat-square)
 
</div>

---
 
## 📚 Table of Contents
 
1. [Setting Up a Repository](#1-setting-up-a-repository)
2. [Saving Changes](#2-saving-changes)
3. [Inspecting a Repository](#3-inspecting-a-repository)
4. [Branching & Tags](#4-branching--tags)
5. [Undoing Changes](#5-undoing-changes)
6. [Rebase vs Merge](#6-rebase-vs-merge)
7. [Reflog — Your Safety Net](#7-reflog--your-safety-net)
8. [🧰 Daily Cheat Sheet](#8-daily-cheat-sheet)
---
 
## 1. Setting Up a Repository
 
### 🆕 `git init`
 
Creates a brand-new Git repo (or turns an existing folder into one). It adds a hidden `.git/` folder that stores all Git's tracking data.
 
```bash
git init
```
 
> 💡 **Production tip:** You'll rarely run `git init` at work — most repos already exist on GitHub/GitLab and you'll `clone` them instead.
 
**Bare repos** (`git init --bare`) have no working files — they only store history. This is how **central/shared repos** (like the ones on GitHub) work internally: you never edit files directly in them, you only `push`/`pull`.
 
---
 
### 📥 `git clone`
 
Downloads a copy of an existing remote repo, including its full history, and automatically sets up a connection to it called `origin`.
 
```bash
git clone <repo-url>                      # clone into a new folder
git clone <repo-url> <folder-name>        # clone into a specific folder
git clone --branch <branch> <repo-url>    # clone a specific branch only
git clone --depth=1 <repo-url>            # shallow clone (latest commit only, no history)
```
 
> ⚡ **Production tip:** `--depth=1` is great in **CI/CD pipelines** — it clones much faster since it skips the entire commit history you don't need to just build/test the code.
 
---
 
### ⚙️ `git config`
 
Sets your identity and personal shortcuts. Run this once per machine.
 
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```
 
**Handy aliases** (shortcuts for commands you'll type constantly):
 
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
```
 
Now you can type `git st` instead of `git status` 🎉
 
---
 
## 2. Saving Changes
 
This is the **core daily loop** every developer repeats dozens of times a day:
 
```
✏️  Edit files  →  ➕ git add  →  📸 git commit  →  📤 git push
```
 
### ➕ `git add` — stage your changes
 
Tells Git *"include this in my next commit."*
 
```bash
git add <file>          # stage one file
git add .                # stage everything changed
git add -p               # interactively choose which chunks to stage (great for clean commits!)
```
 
> 💡 **Production tip:** `git add -p` is a lifesaver when you've made multiple unrelated changes but want to split them into separate, clean commits instead of one messy one.
 
---
 
### 📸 `git commit` — save a snapshot
 
```bash
git commit -m "Fix login bug on Safari"      # commit staged changes with a message
git commit -am "Quick fix"                    # stage ALL tracked changes + commit in one go
git commit --amend                            # edit your last commit (message or content)
```
 
> ⚠️ **Production tip:** Only use `--amend` on commits **you haven't pushed yet**. Amending a pushed/shared commit rewrites history and can break your teammates' branches.
 
**Good commit message habits (used everywhere in real teams):**
 
```
✅ fix: resolve null pointer in payment service
✅ feat: add retry logic to API client
✅ chore: bump docker base image to node:20
❌ "update"
❌ "fixed stuff"
```
 
---
 
### 🔍 `git diff` — see what changed
 
```bash
git diff                 # unstaged changes vs last commit
git diff --staged        # staged changes vs last commit
git diff main..feature   # compare two branches
```
 
---
 
### 🗄️ `git stash` — save work-in-progress without committing
 
Use this when you need to **switch tasks quickly** (e.g., an urgent bug comes in) but aren't ready to commit what you're working on.
 
```bash
git stash                 # shelve your current changes
git stash pop              # bring them back (and remove from stash)
git stash apply             # bring them back (but keep in stash — useful across branches)
git stash list               # see all stashes
git stash show -p stash@{0}   # view the diff of a specific stash
git stash drop stash@{0}       # delete a specific stash
git stash -u                    # also stash untracked (new) files
```
 
> ⚡ **Production tip:** `git stash` is used constantly when a teammate asks you to review a PR or fix a hotfix and you're mid-way through unrelated work — stash it, switch branches, handle the urgent thing, come back, `pop`.
 
---
 
### 🚫 `.gitignore` — stop tracking junk files
 
A `.gitignore` file tells Git which files/folders to **never track** — build artifacts, dependencies, secrets, IDE configs, etc.
 
**Typical production `.gitignore` entries:**
 
```gitignore
node_modules/
dist/
build/
.env
.DS_Store
*.log
__pycache__/
.idea/
.vscode/
```
 
> 🔐 **Critical production rule:** Always `.gitignore` your `.env` files and secrets **before** your first commit. Once a secret is committed, it lives in history forever unless you rewrite it (painful).
 
---
 
## 3. Inspecting a Repository
 
### 📋 `git status`
 
Your most-used command. Shows staged, unstaged, and untracked changes.
 
```bash
git status
```
 
### 🕒 `git log`
 
```bash
git log --oneline                          # compact, one line per commit
git log --oneline --graph --decorate        # visual branch history (very useful!)
git log --author="John"                      # filter by author
git log -p <file>                             # see the changes in each commit for a file
git log --since="2 weeks ago"                  # filter by date
```
 
> 💡 **Production tip:** `git log --oneline --graph --decorate --all` is the command most engineers alias to something short (like `git lg`) because they run it constantly to understand branch history.
 
---
 
## 4. Branching & Tags
 
### 🌿 Branches (the daily workflow)
 
```bash
git branch                       # list local branches
git branch -a                     # list all branches (local + remote)
git checkout -b feature/login      # create + switch to a new branch
git switch feature/login            # switch to an existing branch (modern alternative)
git push -u origin feature/login     # push new branch to remote & track it
git branch -d feature/login           # delete a local branch (after merging)
```
 
> 🏭 **Production workflow (very common):**
> ```
> main (protected, always deployable)
>   └── feature/xyz   → PR → review → merge → deploy
>   └── hotfix/xyz    → urgent fix → PR → merge fast
> ```
 
---
 
### 🏷️ Tags — marking releases
 
Tags mark specific points in history, typically used for **version releases**.
 
```bash
git tag v1.4.0                       # lightweight tag
git tag -a v1.4.0 -m "Release 1.4.0"   # annotated tag (recommended — has metadata)
git push origin v1.4.0                  # push a tag to remote
git tag -d v1.4.0                        # delete a local tag
```
 
> 💡 **Production tip:** Always use **annotated tags** (`-a`) for releases — they store who tagged it, when, and why. This matters for auditing and CI/CD pipelines that trigger deployments off tags (e.g., `v*` triggers a production deploy).
 
---
 
### 🕵️ `git blame` — who changed this line, and why?
 
```bash
git blame -L 10,20 app.py     # show authorship for lines 10–20
```
 
> Useful for tracking down *"why is this weird line here?"* during debugging — usually viewed via GitHub/GitLab's UI rather than the CLI.
 
---
 
## 5. Undoing Changes
 
Different situations need different "undo" strategies — here's the practical decision guide:
 
| Situation | Command | Safe for shared/pushed history? |
|---|---|---|
| Undo an already-pushed commit | `git revert <commit>` | ✅ Yes — creates a new commit that undoes it |
| Undo a local, un-pushed commit | `git reset --soft HEAD~1` | ✅ Yes (local only) |
| Discard local changes completely | `git reset --hard <commit>` | ⚠️ Only if not pushed |
| Remove untracked/junk files | `git clean -fd` | ⚠️ Permanent deletion |
 
### ↩️ `git revert` — the production-safe undo
 
Creates a **new commit** that reverses a previous one. History stays intact — nothing is deleted.
 
```bash
git revert <commit-hash>
```
 
> ✅ **This is the one you use in production.** If a bad commit already went to `main` and others have pulled it, `revert` is the correct tool — it doesn't rewrite history.
 
---
 
### 🔄 `git reset` — the three flavors
 
```bash
git reset --soft <commit>    # move HEAD back, keep changes staged
git reset --mixed <commit>    # move HEAD back, keep changes unstaged (default)
git reset --hard <commit>      # move HEAD back, DELETE all changes — irreversible-feeling
```
 
| Mode | Commit history | Staging area | Working directory |
|---|---|---|---|
| `--soft` | Moved | Unchanged | Unchanged |
| `--mixed` (default) | Moved | Reset | Unchanged |
| `--hard` | Moved | Reset | **Reset (changes lost!)** |
 
> ⚠️ **Golden rule:** Never `reset --hard` or force-push over commits that other people have already pulled. Use `revert` instead for anything public/shared.
 
---
 
### 🧹 `git clean` — remove untracked files
 
```bash
git clean -n     # dry run — see what WOULD be deleted
git clean -f       # actually delete untracked files
git clean -fd        # also delete untracked directories
```
 
> Always run `-n` (dry run) first. There's no undo for `git clean`.
 
---
 
### 🗑️ `git rm` — remove a tracked file
 
```bash
git rm <file>              # delete file + stage the removal
git rm --cached <file>       # stop tracking a file, but keep it on disk (great for accidentally-committed secrets/config)
```
 
---
 
## 6. Rebase vs Merge
 
Both integrate changes from one branch into another — but they behave very differently.
 
| | `git merge` | `git rebase` |
|---|---|---|
| History | Preserves exact history + adds a merge commit | Rewrites commits onto a new base — linear history |
| Safe on shared branches? | ✅ Always safe | ❌ Never rebase commits already pushed/shared |
| Common use | Merging a finished feature branch into `main` | Cleaning up your **own** feature branch before opening a PR |
 
```bash
git merge feature/login          # merge feature into current branch
git rebase main                   # replay your branch's commits on top of latest main
git rebase -i HEAD~3                # interactive rebase — squash/reword/reorder last 3 commits
```
 
**Interactive rebase commands:**
 
```
pick   = keep commit as-is
reword = keep commit, edit message
squash = merge into previous commit
fixup  = like squash, but discard the message
drop   = remove the commit entirely
```
 
> 🏭 **Real-world team habit:** Rebase your feature branch on `main` *before* opening a PR (`git rebase main`) to keep history clean and avoid unnecessary merge commits — but only do this on branches **you own** that haven't been shared yet.
 
---
 
## 7. Reflog — Your Safety Net
 
`git reflog` records every move `HEAD` has made — even commits removed by `reset --hard` or a messy rebase. **Git rarely truly deletes anything immediately.**
 
```bash
git reflog                    # see recent HEAD movements
git reset --hard HEAD@{2}      # jump back to a previous state shown in reflog
```
 
> 🛟 **This is your "oh no" button.** Accidentally did a `reset --hard` and lost commits? Force-pushed and overwrote history? `git reflog` can almost always get you back. Reflog entries expire after ~90 days by default.
 
---
 
## 8. 🧰 Daily Cheat Sheet
 
The commands you'll type **every single day** on the job:
 
```bash
git status                     # what's changed?
git pull                        # get latest from remote
git checkout -b feature/x         # start new work
git add .                          # stage changes
git commit -m "message"             # save snapshot
git push -u origin feature/x          # push branch
git log --oneline --graph --decorate   # visualize history
git stash / git stash pop               # shelve/restore WIP
git diff                                  # review before committing
git revert <hash>                          # undo safely (pushed commits)
git reflog                                  # panic button
```
 
---
 
## ✅ Key Takeaways
 
- 🔁 The daily loop is: **status → add → commit → push**.
- 🛡️ `revert` is safe for shared history; `reset --hard` is not — never use it on pushed commits.
- 🌿 Keep feature branches short-lived; rebase your **own unshared** branch to keep history clean.
- 🏷️ Use **annotated tags** for releases — many CI/CD pipelines trigger off them.
- 🗄️ `git stash` is your best friend for quick context switches.
- 🛟 `git reflog` can save you from almost any local Git disaster.
- 🔐 Never commit secrets — `.gitignore` them from day one.
---
 
<div align="center">
⬅️ [Back to README](../README.md) · ⬅️ [Previous: What is DevOps](./00-what-is-devops-and-how-to-start.md)
 
</div>
 

