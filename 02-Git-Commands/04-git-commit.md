# git commit

## Overview

`git commit` is used to save the changes currently present in the staging area into the local Git repository.

A commit represents a snapshot of the project at a particular point in time.

## Syntax

```bash
git commit -m "commit message"
```

## Basic Example

First, stage the changes:

```bash
git add .
```

Then create a commit:

```bash
git commit -m "Add project files"
```

## How It Works

The Git workflow is:

```text
Working Directory
       |
       | git add
       ↓
Staging Area
       |
       | git commit
       ↓
Local Repository
```

`git commit` only commits changes that have been added to the staging area.

Changes that are still in the working directory will not be included in the commit.

## Commit Message

A commit message should clearly describe the changes made.

Good examples:

```bash
git commit -m "Add login functionality"
git commit -m "Fix database connection"
git commit -m "Update project documentation"
```

Avoid unclear messages such as:

```bash
git commit -m "changes"
git commit -m "update"
git commit -m "done"
```

## Checking Commits

After creating a commit, use:

```bash
git log
```

to view the commit history.

A shorter version of the history can be displayed using:

```bash
git log --oneline
```

## Committing Specific Changes

You can stage a specific file and commit it:

```bash
git add README.md
git commit -m "Update README"
```

Only the changes staged using `git add` are included in the commit.

## Important Points

- `git commit` saves staged changes to the local repository.
- A commit does not automatically upload changes to GitHub.
- A meaningful commit message should describe the changes.
- Changes must normally be staged using `git add` before committing.
- Each commit creates a point in the project's history.
- `git push` is used to upload local commits to a remote repository such as GitHub.

## Interview Question

### What is the purpose of `git commit`?

`git commit` records the changes from the staging area into the local Git repository and creates a new snapshot in the project's history.
