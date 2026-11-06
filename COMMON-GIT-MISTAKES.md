# Common Git Mistakes and How to Fix Them

A quick reference for beginners. Find your problem, read **What you might see**, then follow **Fix**.

**First step for almost every problem:** run `git status`. It tells you where you are and what Git sees.

## Quick index

| # | Problem |
|---|---|
| [1](#1-i-edited-a-file-but-git-does-not-show-it-as-staged) | I edited a file, but Git does not show it as staged |
| [2](#2-i-ran-git-commit-but-git-says-there-is-nothing-to-commit) | I ran `git commit`, but Git says there is nothing to commit |
| [3](#3-i-committed-my-changes-but-they-are-not-on-github) | I committed my changes, but they are not on GitHub |
| [4](#4-git-says-i-am-not-in-a-repository) | Git says I am not in a repository |
| [5](#5-i-accidentally-staged-a-file) | I accidentally staged a file |
| [6](#6-i-staged-the-wrong-changes) | I staged the wrong changes |
| [7](#7-my-remote-repository-url-is-incorrect) | My remote repository URL is incorrect |
| [8](#8-github-says-authentication-failed) | GitHub says authentication failed |
| [9](#9-github-rejects-my-first-push) | GitHub rejects my first push |
| [10](#10-i-do-not-understand-the-difference-between-add-commit-and-push) | I do not understand the difference between add, commit, and push |
| [11](#11-i-do-not-know-what-changed-in-my-file) | I do not know what changed in my file |
| [12](#12-i-want-to-see-my-previous-commits) | I want to see my previous commits |
| [13](#13-i-accidentally-initialized-git-in-the-wrong-folder) | I accidentally initialized Git in the wrong folder |
| [14](#14-i-forgot-my-current-branch-name) | I forgot my current branch name |
| [15](#15-i-want-to-check-whether-my-project-is-connected-to-github) | I want to check whether my project is connected to GitHub |

---

## 1. I edited a file, but Git does not show it as staged

**What you might see:** `git status` lists the file under `Changes not staged for commit`, with the word `modified`.

**Why:** Editing a file does not automatically stage it.

Check:

```bash
git status
```

Fix:

```bash
git add filename
```

Remember: `git add` stages changes.

---

## 2. I ran git commit, but Git says there is nothing to commit

**What you might see:**

```text
no changes added to commit (use "git add" and/or "git commit -a")
```

For a brand-new file, you may see `nothing added to commit but untracked files present` instead.

**Why:** You may have forgotten to stage your changes. Also check that you **saved** the file in your editor.

Fix:

```bash
git status
git add filename
git commit -m "Describe your changes"
```

Your unstaged edits are normally still in your working directory. Git has not deleted them.

---

## 3. I committed my changes, but they are not on GitHub

**What you might see:** GitHub does not show your newest commit. `git status` says:

```text
Your branch is ahead of 'origin/main' by 1 commit.
```

**Why:** A commit saves changes locally. It does not automatically upload them.

Fix:

```bash
git push
```

---

## 4. Git says I am not in a repository

**What you might see:**

```text
fatal: not a git repository (or any of the parent directories): .git
```

**Why:** You may be running the command from the wrong folder.

Check your current directory:

```bash
pwd
```

Move to your project directory:

```bash
cd path/to/your/project
```

Check:

```bash
git status
```

---

## 5. I accidentally staged a file

**What you might see:** `git status` lists the file under `Changes to be committed`, but you do not want it in the next commit.

**Why:** You ran `git add` on the wrong file, or too early.

If you want to unstage a file but keep its edits:

```bash
git restore --staged filename
```

This removes the file from the staging area. It does not discard the working-directory changes.

> **No commits yet?** In a brand-new repository, `git restore --staged` can fail with `fatal: could not resolve HEAD`. Use this instead: `git rm --cached filename`. It also keeps your file and its edits on disk.

---

## 6. I staged the wrong changes

**What you might see:** `git diff --staged` shows changes you did not mean to include, or a file you did not want to commit.

**Why:** You staged a file too early, or staged the wrong file.

Check what is staged:

```bash
git diff --staged
```

Unstage the file:

```bash
git restore --staged filename
```

Then stage the correct file:

```bash
git add correct_filename
```

---

## 7. My remote repository URL is incorrect

**What you might see:** When you push, an error such as:

```text
remote: Repository not found.
fatal: repository 'https://github.com/...' not found
```

**Why:** The URL has a typo (username or repository name), or it points to a repository that does not exist.

Check:

```bash
git remote -v
```

Update it:

```bash
git remote set-url origin YOUR_REPOSITORY_URL
```

Check again:

```bash
git remote -v
```

---

## 8. GitHub says authentication failed

**What you might see:** A message such as:

```text
fatal: Authentication failed for 'https://github.com/...'
```

The wording can vary.

**Why:** GitHub requires supported authentication. Your account password is not accepted for Git commands.

Possible solutions:

- Follow the browser authentication flow.
- Use Git Credential Manager if available.
- Follow your institution's or organization's authentication instructions.

Never share your password or personal access token with another person.

---

## 9. GitHub rejects my first push

**What you might see:**

```text
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to ...
```

**Possible reason:** You created a GitHub repository with a README or another initial file, so the remote repository has a commit that your local repository does not have.

For a beginner workshop, the easiest approach is to create a new empty GitHub repository and repeat the connection process:

```bash
git remote set-url origin NEW_REPOSITORY_URL
git push -u origin main
```

If you need to keep the existing remote content, first learn how to retrieve and reconcile the remote history safely.

Do not use `git push --force` as a quick fix.

---

## 10. I do not understand the difference between add, commit, and push

**What you might see:** You run a command and nothing seems to change on GitHub.

**Why:** Each command does a different job.

Think of the workflow this way:

- `git add`: Select the changes you want to include.
- `git commit`: Save those staged changes locally.
- `git push`: Upload your local commits to the remote repository.

```text
Working directory  --git add-->  Staging area  --git commit-->  Local repository  --git push-->  GitHub
```

---

## 11. I do not know what changed in my file

**What you might see:** You are not sure what Git will save in the next commit.

**Why:** Git only shows changes when you ask it to.

For unstaged changes:

```bash
git diff
```

For staged changes:

```bash
git diff --staged
```

Lines that start with `+` were added. Lines that start with `-` were removed.

---

## 12. I want to see my previous commits

Run:

```bash
git log --oneline
```

This shows a compact history of your commits. Each line has a short commit ID and the commit message. The newest commit is at the top. If the list is long, press `q` to exit.

---

## 13. I accidentally initialized Git in the wrong folder

**What you might see:** `git status` works in a folder where you did not want a repository, or you see `Initialized empty Git repository` in an unexpected location.

**Why:** You ran `git init` before moving into your project folder.

First, confirm your current location:

```bash
pwd
git status
```

If you initialized a repository in the wrong directory, do not delete folders or hidden Git files without understanding what is inside them. Ask for help before removing the `.git` directory.

---

## 14. I forgot my current branch name

Run:

```bash
git branch --show-current
```

`git status` also shows it on the first line, for example `On branch main`.

---

## 15. I want to check whether my project is connected to GitHub

Run:

```bash
git remote -v
```

You should see `origin` and a URL, two times (`fetch` and `push`).

If no remote is displayed, you have not configured one.

---

# Golden rules for beginners

1. Run `git status` frequently.
2. Inspect your changes before committing.
3. Use meaningful commit messages.
4. Remember that commits are local until pushed.
5. Do not use force-push as a troubleshooting shortcut.
6. If you are unsure, inspect before running commands that change or delete things.
