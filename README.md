
# Git & GitHub Workshop: Course Materials

Materials for the beginner **Git & GitHub: Version Control Fundamentals** workshop at Northeastern University Vancouver (Data Analytics Engineering).

This repository contains the learning materials and exercises for both workshop sessions. It is the materials repository, not the repository you will create and work with during the labs.

## What is in this repository

| File | What it is |
|---|---|
| [`SESSION-1-LAB.md`](SESSION-1-LAB.md) | Step-by-step lab for Session 1. Follow it during the workshop. |
| [`COMMON-GIT-MISTAKES.md`](COMMON-GIT-MISTAKES.md) | Quick reference for common Git problems covered in Session 1. |
| [`starter/student_tips.py`](starter/student_tips.py) | Starting Python file used in the Session 1 lab. |
| [`SESSION-2-LAB.md`](SESSION-2-LAB.md) | Step-by-step lab for Session 2, covering branches and pull requests. |
| [`SESSION-2-COMMON-GIT-MISTAKES.md`](SESSION-2-COMMON-GIT-MISTAKES.md) | Quick reference for common problems with branches, pull requests, and merge conflicts. |
| [`student_tips.py`](student_tips.py) | Python example used for Session 2 exercises. |

## Before the workshop

Please prepare these things:

1. Install Git from [git-scm.com](https://git-scm.com). Open a terminal and run `git --version` to check.
2. Create a free account at [github.com](https://github.com). Remember your username.
3. Install a text editor, for example Visual Studio Code.
4. Bring your laptop and charger.

## How to use these files

### Session 1 — Version Control Fundamentals

1. Open [`SESSION-1-LAB.md`](SESSION-1-LAB.md) and follow it in order. Type the commands yourself.
2. In the lab, you create your own `git-workshop` folder and initialize a Git repository.
3. Use the starting Python file from [`starter/student_tips.py`](starter/student_tips.py) when instructed.
4. If something goes wrong, run `git status` first. Then check [`COMMON-GIT-MISTAKES.md`](COMMON-GIT-MISTAKES.md).

> **Important:** The repository you create during the lab is separate from this course materials repository. You create your own repository named `git-workshop` from scratch using `mkdir` and `git init`. Do **not** clone this course materials repository into that folder. Copy the files you need instead.

### Session 2 — Branches, Pull Requests, and Collaboration

1. Continue working with the `git-workshop` repository you created in Session 1.
2. Open [`SESSION-2-LAB.md`](SESSION-2-LAB.md) and follow the exercises.
3. Use `student_tips.py` for practicing feature branches, commits, and pull requests.
4. If something goes wrong, run `git status` first. Then check [`SESSION-2-COMMON-GIT-MISTAKES.md`](SESSION-2-COMMON-GIT-MISTAKES.md).

**Important:** Keep your `git-workshop` repository on GitHub after Session 1. You will need it for Session 2.

## The Python file

`student_tips.py` is intentionally small. The workshop is about Git, not Python. You do not need advanced Python knowledge to complete the exercises.

### Session 1 — Starting version

The initial version contains one study tip:

```python
# student_tips.py

def study_tip():
    print("Practice Git every day!")

study_tip()
```

### Session 1 — Updated version

You add another line during the lab:

```python
# student_tips.py

def study_tip():
    print("Practice Git every day!")
    print("Commit your changes regularly!")

study_tip()
```

### Session 2 — Feature branch version

In Session 2, you create a feature branch and add another study tip:

```python
# student_tips.py

def study_tip():
    print("Practice Git every day!")
    print("Commit your changes regularly!")
    print("Use branches to work on new features!")

study_tip()
```

### Your challenge

Add another useful study or productivity tip inside the `study_tip()` function. Remember to use four spaces of indentation, just like the other lines.

For example:

```python
    print("Review your code before opening a pull request!")
```

To run the file, use:

```bash
python student_tips.py
```

Or, on macOS:

```bash
python3 student_tips.py
```

## Key ideas from the workshop

### Session 1 — Git Fundamentals

- **Git** is a version control tool on your computer.
- **GitHub** is an online platform that hosts Git repositories.
- `git add` stages changes.
- `git commit` saves staged changes locally.
- `git push` uploads your commits to GitHub.
- `git pull` retrieves and integrates remote changes.
- `git clone` copies a remote repository to your computer.
- `git diff` shows changes in your files.
- Run `git status` often.

### Session 2 — Branches and Collaboration

- **Branches** let you work on changes independently from the main branch.
- **Feature branches** are commonly used to develop new features or fix issues.
- `git switch -c` creates and switches to a new branch.
- `git push -u origin branch-name` publishes a new branch to GitHub.
- **Pull requests** allow others to review proposed changes before merging.
- **Merge** combines changes from different branches.
- **Merge conflicts** happen when Git cannot automatically combine changes and requires you to resolve them.

## Security reminder

Never share your GitHub password or personal access token with anyone. Be careful not to commit passwords, API keys, or other sensitive information to a repository.
