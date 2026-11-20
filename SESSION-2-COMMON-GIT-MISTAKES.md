
# Git & GitHub — Session 2
## Common Git Mistakes and Troubleshooting

This guide covers common problems beginners may encounter when working with branches, pull requests, and merge conflicts.

---

## 1. I created a branch, but I am still on `main`

Creating a branch and switching to it are different operations if you use `git branch`.

Check your current branch:

```bash
git branch --show-current
```

Switch to your feature branch:

```bash
git switch feature/add-study-tip
```

Alternatively, create and switch to a new branch in one command:

```bash
git switch -c feature/add-study-tip
```

## 2. Git says the branch already exists

You may have created the branch previously.

List your branches:

```bash
git branch
```

If the branch already exists, switch to it:

```bash
git switch feature/add-study-tip
```

You do not need to create it again.

## 3. I made changes on the wrong branch

First, check your current branch and working directory:

```bash
git branch --show-current
git status
```

Do not immediately reset or delete anything.

If you have uncommitted changes, ask the instructor for help before moving them between branches. If you have already committed changes, avoid rewriting history without guidance.

## 4. Git will not let me switch branches

Git may prevent switching if doing so would overwrite uncommitted changes.

Check the status:

```bash
git status
```

Review your changes:

```bash
git diff
```

If the changes are ready, you can stage and commit them:

```bash
git add student_tips.py
git commit -m "Save current changes"
```

Then switch branches:

```bash
git switch main
```

Do not blindly use commands that discard changes.

## 5. My branch is not visible on GitHub

A branch created locally does not automatically appear on GitHub.

Push it:

```bash
git push -u origin feature/add-study-tip
```

Refresh your GitHub repository page and check the branch list.

## 6. My pull request shows no changes

Check the following:

- Did you select `main` as the base branch?
- Did you select your feature branch as the compare branch?
- Did you commit your changes?
- Did you push your latest commits?
- Has the feature branch already been merged?

You can check your current branch and recent commits:

```bash
git branch --show-current
git log --oneline
```

If you made additional changes after your first push, commit and push them again.

## 7. I cannot create a pull request

Possible reasons include:

- You have not pushed your feature branch.
- You are viewing the wrong GitHub repository.
- You do not have the required repository permissions.
- You are not signed in to the correct GitHub account.

Check that your branch was pushed successfully and ask the repository owner or instructor if you need access.

## 8. GitHub does not let me merge my pull request

Possible reasons include:

- Required reviews have not been completed.
- The repository requires approval from another contributor.
- There are merge conflicts.
- You do not have permission to merge.

Read the message shown by GitHub. Do not try to bypass repository rules.

## 9. I have a merge conflict

A merge conflict means Git cannot automatically combine the changes.

Start by checking the repository status:

```bash
git status
```

Open the file Git identifies as conflicted.

You may see something like:

```text
<<<<<<< HEAD
print("Practice Git consistently!")
=======
print("Practice Git regularly!")
>>>>>>> feature/conflict-demo
```

To resolve it:

1. Read both versions.
2. Decide which version to keep or combine them.
3. Remove all conflict markers.
4. Save the file.
5. Stage the resolved file.
6. Complete the merge.

```bash
git add student_tips.py
git commit -m "Resolve merge conflict"
```

Always check the status afterward:

```bash
git status
```

## 10. What do the conflict markers mean?

| Marker | Meaning |
|---|---|
| `<<<<<<< HEAD` | Beginning of the current branch's version |
| `=======` | Separates the two versions |
| `>>>>>>> branch-name` | End of the incoming branch's version |

These markers are temporary instructions from Git. They must not remain in the final file.

## 11. I accidentally deleted or changed too much while resolving a conflict

Do not commit immediately.

Check the status:

```bash
git status
```

Open the file and review the contents. If you are unsure how to restore the intended changes, ask the instructor before running more commands.

## 12. I want to cancel a merge that is still in progress

If a merge is in progress and you have not completed it, Git may allow you to return to the state before the merge:

```bash
git merge --abort
```

Use this only when a merge is actually in progress. If you are unsure, ask the instructor first.

## 13. My local `main` branch does not show the merged pull request

After merging a pull request on GitHub, your local repository may still have the old version.

Update it:

```bash
git switch main
git pull
```

Then check the commit history:

```bash
git log --oneline
```

## 14. I accidentally committed directly to `main`

First, check what happened:

```bash
git branch --show-current
git log --oneline
git status
```

Do not reset, delete, or rewrite commits without understanding the consequences. Ask the instructor or repository owner for help, especially if you have already pushed the commit.

---

## Safe Troubleshooting Habits

- Run `git status` before taking action.
- Check your current branch with `git branch --show-current`.
- Review changes before staging or committing.
- Read Git's error messages carefully.
- Avoid destructive commands when you are unsure.
- Ask for help before changing commit history.
- Never commit unresolved conflict markers.

**Remember:** Git is designed to help you track changes. Most problems can be investigated safely by checking the status and reviewing your changes first.
