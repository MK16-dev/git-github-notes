# git restore

## Overview

`git restore` is used to restore files in the working directory or remove files from the staging area.

It is commonly used to discard unwanted changes or unstage files before committing.

## Syntax

```bash
git restore <file-name>
```

## Discard Changes in the Working Directory

If a tracked file has been modified and you want to discard those changes:

```bash
git restore README.md
```

This restores `README.md` to its state from the latest commit.

**Warning:** Changes discarded using this command may not be recoverable through normal Git commands.

## Restore Multiple Files

To restore multiple files:

```bash
git restore file1.txt file2.txt
```

To restore all modified files:

```bash
git restore .
```

## Unstage a File

If a file has already been added to the staging area but should not be included in the next commit:

```bash
git restore --staged <file-name>
```

Example:

```bash
git restore --staged README.md
```

This removes the file from the staging area but keeps its changes in the working directory.

## Unstage All Files

To remove all staged files from the staging area:

```bash
git restore --staged .
```

The changes are not deleted; they are simply moved back to the working directory.

## Restore a File from a Specific Commit

A file can also be restored from a specific commit:

```bash
git restore --source=<commit-hash> <file-name>
```

Example:

```bash
git restore --source=8f3a2c1 README.md
```

This restores `README.md` using the version stored in the specified commit.

## Working Directory vs Staging Area

`git restore` can operate on different areas depending on the options used:

```text
Working Directory
       ↑
       | git restore
       |
Staging Area
       ↑
       | git restore --staged
       |
Latest Commit
```

## `git restore` vs `git reset`

| Command | Common Purpose |
|---|---|
| `git restore <file>` | Discard working-directory changes |
| `git restore --staged <file>` | Unstage a file |
| `git reset` | Move HEAD or modify staging/commit state |

`git restore` is generally preferred for straightforward file restoration because its purpose is more specific.

## Important Points

- `git restore` can discard changes in the working directory.
- `git restore --staged` removes files from the staging area without deleting their changes.
- Discarded working-directory changes may be difficult to recover.
- Use `git status` before restoring files to understand their current state.

## Interview Question

### What is the purpose of `git restore`?

`git restore` is used to restore files to a previous state. It can discard working-directory changes or remove files from the staging area using the `--staged` option.
