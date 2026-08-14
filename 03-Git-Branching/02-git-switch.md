# git switch

## Overview

`git switch` is used to switch between Git branches.

It was introduced to provide a more focused command for branch switching, separating this operation from the many other uses of `git checkout`.

## Syntax

```bash
git switch <branch-name>
```

## Switch to an Existing Branch

To switch to an existing branch:

```bash
git switch feature-login
```

Git changes the current working branch to `feature-login`.

You can verify the current branch using:

```bash
git branch
```

The current branch is marked with `*`.

## Create and Switch to a New Branch

To create a new branch and switch to it immediately:

```bash
git switch -c <branch-name>
```

Example:

```bash
git switch -c feature-login
```

This performs two operations:

```text
Create branch
      ↓
Switch to branch
```

## Switch Back to Main

To return to the main branch:

```bash
git switch main
```

If your repository uses `master` instead:

```bash
git switch master
```

## Example Workflow

```bash
git branch
```

Check the available branches.

```bash
git switch -c feature-login
```

Create and switch to a feature branch.

Make changes and commit them:

```bash
git add .
git commit -m "Add login feature"
```

Return to the main branch:

```bash
git switch main
```

## `git switch` vs `git checkout`

| Command | Purpose |
|---|---|
| `git switch <branch>` | Switch to an existing branch |
| `git switch -c <branch>` | Create and switch to a new branch |
| `git checkout <branch>` | Older command that can also switch branches |

`git checkout` has multiple responsibilities, while `git switch` was designed specifically for branch operations.

## Important Points

- `git switch` is used to change the current branch.
- `git switch -c` creates a new branch and switches to it.
- The branch must exist before using `git switch <branch-name>`.
- `git branch` can be used to see the current branch.
- `git checkout` can also switch branches, but `git switch` is the more focused modern command.

## Interview Question

### What is the purpose of `git switch`?

`git switch` is used to switch from one Git branch to another. It can also create and switch to a new branch using the `-c` option.

### How do you create and switch to a branch in one command?

```bash
git switch -c feature-login
```
