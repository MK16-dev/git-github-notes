# git status

## Overview

`git status` displays the current state of the working directory and staging area.

It shows which files have been modified, added, deleted, or are currently untracked.

## Syntax

```bash
git status
```

## Example

Run the following command inside a Git repository:

```bash
git status
```

Example output:

```text
On branch main

Changes not staged for commit:
  modified:   README.md

Untracked files:
  notes.txt
```

## Understanding the Output

### Modified Files

A file that was previously tracked by Git but has been changed is shown as modified.

```text
Changes not staged for commit:
  modified:   README.md
```

### Untracked Files

A new file that Git has not started tracking is shown as untracked.

```text
Untracked files:
  notes.txt
```

### Staged Files

After using `git add`, files are moved to the staging area.

```bash
git add README.md
git status
```

Git will show the file under:

```text
Changes to be committed:
```

## Working Directory and Staging Area

`git status` helps identify the difference between:

```text
Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
  git commit
       ↓
Local Repository
```

## Common Usage

Check the repository status before making changes:

```bash
git status
```

Check which files have been modified:

```bash
git status
```

Check which files are staged before committing:

```bash
git status
```

## Important Points

- `git status` does not modify any files.
- It shows the current state of the working directory and staging area.
- It helps identify modified, staged, deleted, and untracked files.
- It should commonly be used before `git add` and `git commit`.

## Interview Question

### What is the purpose of `git status`?

`git status` displays the current state of the working directory and staging area, including modified, staged, deleted, and untracked files.
