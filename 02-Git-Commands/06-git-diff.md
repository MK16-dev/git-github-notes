# git diff

## Overview

`git diff` is used to view the differences between different states of a Git repository.

It helps identify what has been added, modified, or removed before changes are staged or committed.

## Syntax

```bash
git diff
```

## View Unstaged Changes

To view changes made in the working directory that have not been staged:

```bash
git diff
```

For example, if a tracked file is modified:

```text
Working Directory
       |
       | git diff
       ↓
View changes that are not staged
```

## View Staged Changes

To view changes that have already been added to the staging area:

```bash
git diff --staged
```

You can also use:

```bash
git diff --cached
```

Both commands display the differences between the staging area and the latest commit.

## Compare a Specific File

To view changes in a specific file:

```bash
git diff README.md
```

This displays only the unstaged changes made to `README.md`.

## Compare Two Commits

To compare two commits:

```bash
git diff <commit-hash-1> <commit-hash-2>
```

Example:

```bash
git diff 8f3a2c1 4d7b91e
```

This shows the differences between the two specified commits.

## Understanding the Output

A typical `git diff` output may look like:

```text
-Old line
+New line
```

- Lines beginning with `-` indicate removed content.
- Lines beginning with `+` indicate added content.

## Git Diff in the Git Workflow

```text
Working Directory
       |
       | git diff
       ↓
Review unstaged changes
       |
       | git add
       ↓
Staging Area
       |
       | git diff --staged
       ↓
Review staged changes
       |
       | git commit
       ↓
Local Repository
```

## Useful Commands

| Command | Purpose |
|---|---|
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git diff --cached` | Show staged changes |
| `git diff <file>` | Show changes in a specific file |
| `git diff <commit1> <commit2>` | Compare two commits |

## Important Points

- `git diff` helps review changes before committing.
- `git diff` shows unstaged changes by default.
- `git diff --staged` shows changes that are ready to be committed.
- Reviewing differences helps prevent unintended changes from being committed.

## Interview Question

### What is the difference between `git diff` and `git diff --staged`?

`git diff` shows changes in the working directory that have not been staged, while `git diff --staged` shows changes that have already been added to the staging area and are ready to be committed.
