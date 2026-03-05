# Git Lab – Commits, Reset, Amend, and Revert

## Overview

This repository demonstrates several important Git operations including:

* Creating multiple commits
* Deleting commits using reset
* Creating new commits
* Amending commits
* Reverting commits

All operations were performed using a simple file called `file.txt`.

---

# 1. Creating 4 Commits

First, a file was created and modified several times.
Each modification was committed separately.

### Commands

```bash
echo "line 1" >> file.txt
git add file.txt
git commit -m "commit 1"

echo "line 2" >> file.txt
git add file.txt
git commit -m "commit 2"

echo "line 3" >> file.txt
git add file.txt
git commit -m "commit 3"

echo "line 4" >> file.txt
git add file.txt
git commit -m "commit 4"
```

### Check commits

```bash
git log --oneline
```

Expected output example:

```
commit4
commit3
commit2
commit1
```

---

# 2. Deleting the Last Two Commits

To remove the last two commits from the repository history, the following command was used:

```bash
git reset --hard HEAD~2
```

Explanation:

* `HEAD` = the latest commit
* `HEAD~2` = go back two commits
* `--hard` = remove commits and reset the working directory

After this command the history becomes:

```
commit2
commit1
```

---

# 3. Creating a New Commit After Deletion

A new change was added to the file after deleting the previous commits.

### Commands

```bash
echo "new change after deletion" >> file.txt
git add file.txt
git commit -m "commit after deletion"
```

Now the commit history looks like:

```
commit after deletion
commit2
commit1
```

---

# 4. Amending the Last Commit

The text **"lab Done"** was added to the file, then the last commit was amended.

### Commands

```bash
echo "lab Done" >> file.txt
git add file.txt
git commit --amend
```

This command modifies the **most recent commit**.

---

# 5. Changing the Commit Message

The last commit message was updated to **finish**.

```bash
git commit --amend -m "finish"
```

Now the final commit message becomes:

```
finish
```

---

# What is Git Revert?

`git revert` is used to undo a commit **without deleting the commit history**.

Instead of removing commits, Git creates a **new commit that reverses the changes** made by a previous commit.

### Example

```bash
git revert HEAD
```

This command creates a new commit that undoes the last commit.

Benefits of revert:

* Keeps full commit history
* Safe for shared repositories
* Recommended when working with teams

---

# Bonus Task – Revert 3 Commits Back

To undo the last three commits, the following command can be used:

```bash
git revert HEAD~2..HEAD
```

Explanation:

* `HEAD` → latest commit
* `HEAD~2` → third commit before the latest
* Git creates new commits that reverse the changes.

Alternative method:

```bash
git revert HEAD
git revert HEAD~1
git revert HEAD~2
```

Each command creates a new commit that cancels the previous changes.

---

# Useful Git Commands

Check commit history:

```bash
git log --oneline
```

Push changes to GitHub:

```bash
git push origin main
```

Force push (after reset or amend):

```bash
git push --force
```

---

# Author

Marten Wafik
