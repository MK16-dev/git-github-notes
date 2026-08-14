# git checkout

## Overview

`git checkout` is a Git command that can be used to switch branches and, in older Git workflows, create and switch to branches.

Although `git switch` is now the more focused command for branch switching, `git checkout` is still widely used and important to understand.

## Switch to an Existing Branch

To switch to an existing branch:

```bash
git checkout main
```

This changes the current branch to `main`.

You can verify the current branch using:

```bash
git branch
```

The current branch is marked with `*`.

## Create and Switch to a New Branch

To create a new branch and switch to it in one command:

```bash
git checkout -b feature2
```

This is equivalent to:

```bash
git branch feature2
git checkout feature2
```

## Example

Start by checking the available branches:

```bash
git branch
```

Create and switch to a new feature branch:

```bash
git checkout -b feature2
```

Make changes to the project and commit them:

```bash
git add .
git commit -m "Add feature2 changes"
```

Switch back to the main branch:

```bash
git checkout main
```

## `git checkout` vs `git switch`

| Command | Purpose |
|---|---|
| `git checkout main` | Switch to the `main` branch |
| `git checkout -b feature2` | Create and switch to `feature2` |
| `git switch main` | Switch to the `main` branch |
| `git switch -c feature2` | Create and switch to `feature2` |

`git switch` was introduced to provide a clearer command specifically for branch switching.

However, `git checkout` remains important because it is commonly encountered in existing projects and Git documentation.

## Important Points

- `git checkout <branch>` switches to an existing branch.
- `git checkout -b <branch>` creates and switches to a new branch.
- `git switch` is the more focused command for branch switching.
- `git checkout` has additional uses beyond branch switching, including restoring files in older Git workflows.

## Interview Question

### How do you create and switch to a new branch using `git checkout`?

Use:

```bash
git checkout -b feature2
```

This creates the `feature2` branch and switches to it immediately.
