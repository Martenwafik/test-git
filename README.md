# Git Lab – Commits, Reset, Amend, and Revert

## Overview

This repository demonstrates basic Git operations including:

* Creating commits
* Deleting commits
* Amending commits
* Reverting changes

All operations were performed using a simple text file.

---

## Steps Performed

### 1. Create 4 Commits

Four commits were created by modifying `newfile.txt` and committing the changes.

#### Commands

```bash
echo "MY NAME IS MARTEN WAFIK ROSHDY" >> newfile.txt
git add newfile.txt
git commit -m "adding my full name"

echo "MY AGE IS 24" >> newfile.txt
git commit -am "adding my age (commit 2)"

echo "MY TRACK IS SYSTEM ADMIN" >> newfile.txt
git commit -am "adding my track (commit 3)"

echo "MY COURSE IS GIT" >> newfile.txt
git commit -am "adding my course (commit 4)"
```

#### Check commits

```bash
git log --oneline
```

---

### 2. Delete the Last Two Commits

The last two commits were removed using:

```bash
git reset --hard HEAD~2
```

Explanation:

* `HEAD` refers to the latest commit.
* `HEAD~2` means going back two commits.
* `--hard` removes the commits and resets the working directory.

---

### 3. Add a New Commit

A new change was added after deletion with the commit message **"commit after deletion"**.

```bash
echo "COMMIT AFTER DELETION" >> newfile.txt
git commit -am "commit after deletion"
```

---

### 4. Amend the Last Commit

The text **"lab Done"** was added to the file and the last commit was amended.

```bash
echo "lab Done" >> newfile.txt
git add newfile.txt
git commit --amend
```

---

### 5. Change the Commit Message

The amended commit message was updated to **finish**.

```bash
git commit --amend -m "finish"
```

---

## Revert Concept

`git revert` is used to undo a commit by creating a **new commit** that reverses the changes made by a previous commit.

Unlike `git reset`, it **does not remove commit history**.

Example:

```bash
git revert HEAD
```

This command creates a new commit that cancels the changes from the latest commit.

---

## Bonus Task

Revert three commits back using:

```bash
git revert HEAD~2..HEAD
```

This command creates new commits that reverse the changes made in the last three commits.

---

## Author

Marten Wafik
