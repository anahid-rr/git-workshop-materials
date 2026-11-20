
# Git & GitHub — Session 2 Lab
## Branches, Pull Requests, and Collaboration

**Goal:** Practice using Git branches, pushing a feature branch to GitHub, and creating a pull request.

**Before you start:** You should have Git installed, a GitHub account, and access to your repository from Session 1.

---

## Part 1 — Check Your Repository

Open your terminal or VS Code terminal and navigate to your workshop repository.

```bash
cd path/to/git-workshop
```

Check your current repository status:

```bash
git status
git branch
git branch --show-current
```

Make sure you are in the correct repository and that you do not have unfinished changes from Session 1.

If you have uncommitted work, review it before continuing. Do not discard changes just to start the lab.

## Part 2 — Create a Feature Branch

A branch lets you work on a new feature without directly changing the main branch.

Create a branch called `feature/add-study-tip`:

```bash
git switch -c feature/add-study-tip
```

Verify that you are on the new branch:

```bash
git branch --show-current
```

Expected output:

```text
feature/add-study-tip
```

## Part 3 — Make a Change

Open `student_tips.py` and add another print statement inside the `study_tip()` function:

```python
def study_tip():
    print("Practice Git every day!")
    print("Commit your changes regularly!")
    print("Use branches to work on new features!")

study_tip()
```

Save the file.

Check what changed:

```bash
git status
git diff
```

Stage the file:

```bash
git add student_tips.py
```

Review the staged changes:

```bash
git diff --staged
```

Commit your change:

```bash
git commit -m "Add branch study tip"
```

Check your recent commits:

```bash
git log --oneline
```

## Part 4 — Push Your Branch to GitHub

Push your feature branch:

```bash
git push -u origin feature/add-study-tip
```

The `-u` option connects your local branch to the remote branch on GitHub. You can usually use `git push` for later pushes from this branch.

Open your repository on GitHub and check that your new branch is visible.

**Remember:** Pushing a branch uploads your commits to GitHub. It does not merge the branch into `main`.

## Part 5 — Create a Pull Request

A pull request (PR) asks other contributors to review your changes before they are merged into the main branch.

On GitHub:

1. Open your repository.
2. Select **Pull requests**.
3. Select **New pull request**.
4. Set the base branch to `main`.
5. Set the compare branch to `feature/add-study-tip`.
6. Review the changes.
7. Select **Create pull request**.
8. Add a meaningful title and a short description.

Example title:

`Add a new study tip`

Example description:

`Added a new print statement to the study_tip() function.`

If you are working with a partner, ask them to review your pull request.

If you have permission and the repository allows it, merge the pull request.

## Part 6 — Update Your Local Main Branch

After the pull request is merged on GitHub, update your local repository:

```bash
git switch main
git pull
```

Check your recent commits:

```bash
git log --oneline
```

Your local `main` branch should now include the merged change.

---

## Part 7 — Understanding Merge Conflicts

A merge conflict happens when Git cannot automatically combine changes.

For example, imagine two people edit the same line in `student_tips.py`.

The original line:

```python
print("Practice Git every day!")
```

One person changes it to:

```python
print("Practice Git regularly!")
```

Another person changes it to:

```python
print("Practice Git consistently!")
```

Git may not know which version should be kept.

A conflict can look like this:

```text
<<<<<<< HEAD
print("Practice Git consistently!")
=======
print("Practice Git regularly!")
>>>>>>> feature/conflict-demo
```

### How to resolve a conflict

1. Open the file containing the conflict.
2. Read both versions.
3. Decide which version to keep, or combine the changes.
4. Remove the conflict markers (`<<<<<<<`, `=======`, and `>>>>>>>`).
5. Save the file.
6. Stage the resolved file.
7. Complete the merge commit if Git requires one.

Example of a resolved line:

```python
print("Practice Git every day and commit your changes regularly!")
```

Then run:

```bash
git status
git add student_tips.py
git commit -m "Resolve study tip merge conflict"
```

**Important:** Do not commit a file while conflict markers remain in it.

For this workshop, follow the instructor's separate conflict demonstration. Do not intentionally create a conflict in your main workshop repository unless instructed.

---

## Optional Challenge — Add Another Feature

Create another feature branch:

```bash
git switch -c feature/add-productivity-tip
```

Add another useful tip to `student_tips.py`, such as:

```python
print("Review your code before opening a pull request!")
```

Then:

1. Check your changes with `git diff`.
2. Stage the file.
3. Commit your changes.
4. Push your branch.
5. Create a pull request.
6. Ask a partner to review your changes.

---

## Quick Reference

| Task | Command |
|---|---|
| List branches | `git branch` |
| Check current branch | `git branch --show-current` |
| Create and switch branch | `git switch -c branch-name` |
| Switch branches | `git switch branch-name` |
| Check changes | `git status` |
| Review unstaged changes | `git diff` |
| Stage a file | `git add filename` |
| Review staged changes | `git diff --staged` |
| Commit changes | `git commit -m "message"` |
| Push a new branch | `git push -u origin branch-name` |
| Pull latest changes | `git pull` |
| View commit history | `git log --oneline` |

**Lab complete!** You have practiced creating a branch, committing changes, pushing to GitHub, and creating a pull request.
