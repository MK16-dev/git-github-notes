# git restore

## Overview

`git restore` is used to restore files in the working directory or staging area.

It is mainly used to discard or undo changes that have not yet been committed.

`git restore` was introduced as a clearer alternative to using some forms of `git checkout` for restoring files.

## Restore a Modified File

Suppose a tracked file has been modified:

```text
README.md
```

To discard the changes in the working directory:

```bash
git restore README.md
```

This restores the file to the version from the current commit.

Any uncommitted changes in that file will be discarded.

## Restore All Modified Files

To restore all modified tracked files:

```bash
git restore .
```

Use this carefully because uncommitted changes will be discarded.

## Unstage a File

If a file has already been staged using:

```bash
git add file.txt
```

you can remove it from the staging area with:

```bash
git restore --staged file.txt
```

The file remains modified in the working directory, but it is no longer staged.

## Unstage All Files

To unstage all staged files:

```bash
git restore --staged .
```

This removes the files from the staging area without deleting the changes from the working directory.

## Restore and Unstage

The `--staged` option tells Git to restore the version in the staging area.

Without `--staged`:

```bash
git restore file.txt
```

restores the working directory.

With `--staged`:

```bash
git restore --staged file.txt
```

removes the file from the staging area.

## Restore from a Specific Commit

A file can also be restored from a specific commit:

```bash
git restore --source=<commit> file.txt
```

Example:

```bash
git restore --source=HEAD~1 README.md
```

This restores `README.md` using the version from the previous commit.

## Restore vs Reset

These commands can both be used when undoing changes, but they serve different purposes.

### `git restore`

Primarily works with files in the working directory and staging area.

Example:

```bash
git restore file.txt
```

### `git reset`

Can move the current branch or `HEAD` to another commit and can also change the staging area.

Example:

```bash
git reset HEAD~1
```

A simple way to remember:

```text
git restore
    ↓
Restore files

git reset
    ↓
Move HEAD / change staging state
```

## Restore vs Revert

These commands also have different purposes.

### `git restore`

Used mainly for uncommitted file changes.

### `git revert`

Creates a new commit that reverses the effect of an earlier commit.

Example:

```bash
git revert <commit-hash>
```

Therefore:

```text
Uncommitted changes
        ↓
   git restore

Committed changes
        ↓
   git revert
```

## Important Points

- `git restore` is used to restore files.
- `git restore file.txt` discards unstaged changes in a file.
- `git restore --staged file.txt` unstages a file without discarding its working-directory changes.
- `git restore .` restores all modified tracked files.
- Be careful when using `git restore` because discarded uncommitted changes may not be recoverable.
- `git restore` is different from `git reset` and `git revert`.

## Interview Questions

### What does `git restore` do?

`git restore` restores files in the working directory or staging area to a specified state.

### How do you discard changes made to a file?

```bash
git restore file.txt
```

### How do you unstage a file?

```bash
git restore --staged file.txt
```

### Does `git restore --staged` delete the changes?

No. It removes the file from the staging area but keeps the changes in the working directory.

### What is the difference between `git restore` and `git revert`?

`git restore` is mainly used for restoring uncommitted file changes, while `git revert` creates a new commit that reverses the changes introduced by an earlier commit.
