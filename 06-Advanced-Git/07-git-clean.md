# git clean

## Overview

`git clean` is used to remove untracked files and directories from a working directory.

It is useful when a repository contains files that Git is not tracking and those files are no longer needed.

Unlike `git restore`, which works with tracked file changes, `git clean` primarily deals with untracked files.

## Check Untracked Files First

Before removing anything, preview what would be deleted:

```bash
git clean -n
```

or:

```bash
git clean --dry-run
```

Example:

```text
Would remove temp.txt
Would remove test.txt
```

The `-n` option performs a dry run and does not delete anything.

## Remove Untracked Files

To remove untracked files:

```bash
git clean -f
```

The `-f` option means force.

Git requires this option because deleting files is a destructive operation.

## Remove Untracked Directories

To remove untracked directories as well:

```bash
git clean -fd
```

Here:

- `-f` → force removal
- `-d` → include untracked directories

## Remove Ignored Files

By default, ignored files are not removed.

To also remove ignored files:

```bash
git clean -fX
```

This removes ignored files but keeps other untracked files.

## Remove All Untracked and Ignored Files

To remove both untracked and ignored files:

```bash
git clean -fx
```

This is highly destructive and should be used carefully.

## Typical Workflow

A safer workflow is:

```bash
git status
```

Check which files are untracked.

Then preview what would be removed:

```bash
git clean -n
```

If the listed files are definitely unnecessary:

```bash
git clean -f
```

For untracked directories:

```bash
git clean -fd
```

## git clean vs git restore

These commands solve different problems.

### `git restore`

Used mainly to discard changes to tracked files.

```bash
git restore file.txt
```

### `git clean`

Used to remove untracked files.

```bash
git clean -f
```

A simple way to remember:

```text
Tracked file changes
        ↓
   git restore

Untracked files
        ↓
    git clean
```

## git clean vs git reset

### `git clean`

Removes untracked files and directories.

### `git reset`

Changes the staging area and, depending on the mode, can move `HEAD` or modify tracked files.

They are not interchangeable.

## Important Points

- `git clean` removes untracked files.
- `git clean -n` previews what would be removed.
- `git clean -f` removes untracked files.
- `git clean -fd` also removes untracked directories.
- `git clean -fX` removes ignored files.
- `git clean -fx` removes both ignored and untracked files.
- Always use `git clean -n` before using a destructive option.
- `git clean` does not remove normal committed files.

## Interview Questions

### What does `git clean` do?

`git clean` removes untracked files and directories from the working directory.

### What does `git clean -n` do?

It performs a dry run and shows which files would be removed without actually deleting them.

### What does `git clean -f` do?

It forcefully removes untracked files.

### What does `git clean -fd` do?

It removes untracked files and untracked directories.

### Why should `git clean` be used carefully?

Because files removed by `git clean` are not placed in the Git history and may not be recoverable through Git.
