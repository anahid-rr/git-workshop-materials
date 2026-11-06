# Git & GitHub Workshop: Course Materials

Materials for the beginner **Git & GitHub: Version Control Fundamentals** workshop at Northeastern University Vancouver (Data Analytics Engineering).

This repository holds the files you need during Session 1. It is not the repository you will create in the lab.

## What is in this repository

| File | What it is |
|---|---|
| [`SESSION-1-LAB.md`](SESSION-1-LAB.md) | Step-by-step lab for Session 1. Follow it during the workshop. |
| [`COMMON-GIT-MISTAKES.md`](COMMON-GIT-MISTAKES.md) | Quick reference for common Git problems and how to fix them. |
| [`starter/student_tips.py`](starter/student_tips.py) | The small Python file you will track with Git in the lab. |

## Before the workshop

Please prepare these things:

1. Install Git from [git-scm.com](https://git-scm.com). Open a terminal and run `git --version` to check.
2. Create a free account at [github.com](https://github.com). Remember your username.
3. Install a text editor, for example Visual Studio Code.
4. Bring your laptop and charger.

## How to use these files

1. Open [`SESSION-1-LAB.md`](SESSION-1-LAB.md) and follow it in order. Type the commands yourself.
2. In Part 3 of the lab, you create `student_tips.py` yourself. You can copy the code from the lab or from [`starter/student_tips.py`](starter/student_tips.py).
3. If something goes wrong, run `git status` first. Then check [`COMMON-GIT-MISTAKES.md`](COMMON-GIT-MISTAKES.md).

> **Important:** In the lab, you create your own repository named `git-workshop` from scratch with `mkdir` and `git init`. Do **not** clone this repository into that folder. Copy the files you need instead.

## The Python file

`student_tips.py` is intentionally small. The workshop is about Git, not Python.

**Starting version** (the file in `starter/`):

```python
# student_tips.py

def study_tip():
    print("Practice Git every day!")

study_tip()
```

**Second version** (you add this in Part 6 of the lab):

```python
# student_tips.py

def study_tip():
    print("Practice Git every day!")
    print("Commit your changes regularly!")

study_tip()
```

**Your challenge** (Part 10 of the lab): add a third line inside the function, with four spaces of indentation like the other lines. For example:

```python
    print("Write meaningful commit messages!")
```

To run the file, use `python student_tips.py` (or `python3 student_tips.py` on macOS).

## Key ideas from Session 1

- **Git** is a version control tool on your computer. **GitHub** is an online platform that hosts Git repositories.
- `git add` stages changes.
- `git commit` saves staged changes locally.
- `git push` uploads your commits to GitHub.
- `git clone` copies a remote repository to your computer.
- Run `git status` often.

## Session 2 preview

In Session 2, we build on the repository you create today:

- Branches
- Pull requests
- Collaboration
- Merge conflicts

Please keep your `git-workshop` repository on GitHub.

## Security reminder

Never share your GitHub password or personal access token with anyone.
