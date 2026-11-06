# Git & GitHub Workshop — Session 1 Lab

## Goal

In this lab, you will:

- Create a local Git repository.
- Create and edit a Python file.
- Track changes using Git.
- Stage and commit changes.
- Connect your repository to GitHub.
- Push your work to GitHub.
- Clone a repository.

**How to use this lab:** Work through the parts in order. Type the commands yourself. After each command, read the output. If something looks wrong, run `git status` and ask for help.

---

## Part 1: Check Git installation

Open your terminal and run:

```bash
git --version
```

If Git is installed, you should see its version, for example `git version 2.xx.x`.

Configure your identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Check your configuration:

```bash
git config --list
```

Use the name and email you want associated with your commits. If possible, use the same email as your GitHub account.

> These commands print nothing when they work. No message means success. If the `--list` output is long, press `q` to exit.

---

## Part 2: Create a project

Run:

```bash
mkdir git-workshop
cd git-workshop
git init
```

Check the repository:

```bash
git status
```

You should see `On branch main` and `No commits yet`.

You have now created a local Git repository.

> If you see `On branch master`, that is fine. You will rename it to `main` in Part 8.

---

## Part 3: Create a Python file

Create a file named `student_tips.py` in your project folder (`git-workshop`).

Add this code:

```python
# student_tips.py

def study_tip():
    print("Practice Git every day!")

study_tip()
```

Save the file.

Check the status:

```bash
git status
```

Git should show the new file as untracked.

---

## Part 4: Stage your file

Run:

```bash
git add student_tips.py
git status
```

The file should now be staged. Look for `Changes to be committed`.

Remember:

- `git add` stages a change.
- It does not create a commit.

---

## Part 5: Inspect and commit

Run:

```bash
git diff --staged
```

Review the changes. Lines that start with `+` are lines you added.

Now commit:

```bash
git commit -m "Add study tip"
```

Check your commit history:

```bash
git log --oneline
```

You should see one commit with the message `Add study tip`.

You have created your first commit!

---

## Part 6: Modify your file

Add another print statement:

```python
# student_tips.py

def study_tip():
    print("Practice Git every day!")
    print("Commit your changes regularly!")

study_tip()
```

Save the file.

Run:

```bash
git status
git diff
```

Notice that `git diff` displays changes that have not yet been staged.

Stage the changes:

```bash
git add student_tips.py
git diff --staged
```

Commit:

```bash
git commit -m "Add another study tip"
```

Check your history again:

```bash
git log --oneline
```

You should now see two commits.

---

## Part 7: Create a GitHub repository

1. Sign in to GitHub.
2. Select **New repository**.
3. Name it `git-workshop`.
4. Choose Public or Private.
5. Leave the README, `.gitignore`, and license options unchecked for this exercise. The repository must stay empty.
6. Create the repository.

Copy the repository URL (choose the HTTPS URL).

---

## Part 8: Connect your local repository to GitHub

Make sure your terminal is inside the `git-workshop` folder.

Replace `YOUR_REPOSITORY_URL` with your actual GitHub repository URL.

```bash
git remote add origin YOUR_REPOSITORY_URL
git remote -v
```

You should see your URL two times, one for `fetch` and one for `push`.

Rename the current branch:

```bash
git branch -M main
```

Push your code:

```bash
git push -u origin main
```

GitHub may ask you to sign in. Follow the sign-in steps on the screen. Do not share your password or token with anyone.

Open your GitHub repository in the browser and refresh the page. You should see your Python file and commits.

---

## Part 9: Clone a repository

Move outside your project folder:

```bash
cd ..
```

Clone your repository into a new folder named `git-workshop-clone`:

```bash
git clone YOUR_REPOSITORY_URL git-workshop-clone
```

> A folder named `git-workshop` already exists on your computer. The extra name `git-workshop-clone` makes Git create a separate copy.

A new folder should be created containing your repository. Look inside it:

```bash
cd git-workshop-clone
git log --oneline
```

You should see the same commits as in your original project.

Now go back to your original project for the challenge:

```bash
cd ../git-workshop
```

---

## Part 10: Your challenge

Now work independently. Work in your original `git-workshop` folder.

1. Open `student_tips.py`.
2. Add a third study tip. Save the file.
3. Run `git status`.
4. Run `git diff`.
5. Stage the file.
6. Run `git diff --staged`.
7. Commit with a meaningful commit message.
8. Push your changes to GitHub with `git push`.
9. Open GitHub and verify your changes.

---

## Quick command reference

| Command | Purpose |
|---|---|
| `git --version` | Check Git installation |
| `git init` | Create a repository |
| `git status` | Check repository status |
| `git add filename` | Stage a file |
| `git diff` | Inspect unstaged changes |
| `git diff --staged` | Inspect staged changes |
| `git commit -m "message"` | Create a commit |
| `git log --oneline` | View commit history |
| `git remote -v` | View remote repositories |
| `git push` | Upload commits |
| `git pull` | Retrieve and integrate remote changes |
| `git clone URL` | Copy a remote repository |

---

## Common problems

| What you see | What to try |
|---|---|
| `nothing to commit` or `no changes added to commit` | Did you save the file? Did you run `git add`? Check `git status`. |
| `fatal: not a git repository` | You are in the wrong folder. Run `pwd`, then `cd` into `git-workshop`. |
| Your commit is not on GitHub | You may have forgotten to push. Run `git push`. |
| Push fails with "repository not found" | Check the URL with `git remote -v`. To fix it, run `git remote set-url origin YOUR_REPOSITORY_URL`. |
| `destination path ... already exists` when cloning | Add a new folder name at the end of the clone command, as in Part 9. |

If you are still stuck, raise your hand or ask a neighbor.

---

## Important reminders

- Save your file before checking Git status.
- A staged change is not yet committed.
- A commit is local until you push it.
- Always check `git status` if you are unsure what is happening.
- Write meaningful commit messages.
- Never share your GitHub password or personal access token.

Congratulations! You have completed Session 1.
