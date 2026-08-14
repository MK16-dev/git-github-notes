# git branch

## Overview

A Git branch is an independent line of development within a repository.

Branches allow developers to work on different features, fixes, or experiments without directly affecting the main branch.

The `git branch` command is used to create, list, rename, and delete branches.

## List Branches

To view the branches in the current repository:

```bash
git branch
```

Example:

```text
* main
  feature-login
  bug-fix
```

The `*` indicates the branch currently checked out.

## Create a Branch

To create a new branch:

```bash
git branch <branch-name>
```

Example:

```bash
git branch feature-login
```

This creates the branch but does not switch to it.

## Create and Switch to a Branch

A branch can be created and switched to using:

```bash
git switch -c <branch-name>
```

Example:

```bash
git switch -c feature-login
```

This creates `feature-login` and switches to it immediately.

## Switch Between Branches

To switch to an existing branch:

```bash
git switch <branch-name>
```

Example:

```bash
git switch main
```

## Delete a Branch

To delete a branch that has already been merged:

```bash
git branch -d <branch-name>
```

Example:

```bash
git branch -d feature-login
```

To force-delete a branch that has not been merged:

```bash
git branch -D <branch-name>
```

Use `-D` carefully because it can delete commits that have not been merged elsewhere.

## Rename a Branch

To rename the current branch:

```bash
git branch -m <new-name>
```

Example:

```bash
git branch -m main
```

A common use is renaming the default branch from `master` to `main`:

```bash
git branch -m master main
```

## Branch Workflow

A typical feature development workflow is:

```text
main
 |
 | git switch -c feature-login
 ↓
feature-login
 |
 | Develop and commit changes
 ↓
feature-login
 |
 | Merge into main
 ↓
main
```

The feature branch allows development to happen separately from the main branch.

## `git branch` vs `git switch`

| Command | Purpose |
|---|---|
| `git branch` | Create, list, rename, or delete branches |
| `git switch` | Switch between branches |

## Important Points

- A branch is a separate line of development.
- `git branch` creates and manages branches.
- Creating a branch does not automatically switch to it.
- `git switch` is used to move between branches.
- `git switch -c` creates and switches to a new branch.
- The `main` branch is commonly used as the primary branch.
- Branches allow multiple features or fixes to be developed independently.

## Interview Question

### What is a Git branch?

A Git branch is an independent line of development that allows changes to be developed separately from other branches.

### Does `git branch <branch-name>` switch to the new branch?

No. `git branch <branch-name>` only creates the branch. To switch to it, use:

```bash
git switch <branch-name>
```

Or create and switch to it at the same time:

```bash
git switch -c <branch-name>
```
