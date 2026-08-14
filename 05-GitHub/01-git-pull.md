# git pull

## Overview

`git pull` is used to download changes from a remote repository and integrate them into the current local branch.

It is commonly used when changes have been pushed to a remote repository by another developer or from another local environment.

## Syntax

```bash
git pull <remote> <branch>
```

Example:

```bash
git pull origin main
```

Here:

- `git pull` downloads and integrates remote changes.
- `origin` is the name of the remote repository.
- `main` is the branch from which changes are pulled.

## Pull Changes from a Specific Branch

To pull the latest changes from `feature1`:

```bash
git pull origin feature1
```

This fetches the changes from `origin/feature1` and integrates them into the current branch.

The current branch matters.

For example, if you are currently on `main`:

```bash
git checkout main
git pull origin feature1
```

Git attempts to integrate the changes from `feature1` into your current `main` branch.

## Pull Without Specifying Remote and Branch

If the current branch has an upstream branch configured, you can simply use:

```bash
git pull
```

Git uses the configured upstream branch automatically.

For example:

```text
Local main
    ↓
origin/main
```

After the upstream relationship is configured:

```bash
git pull
```

will pull from the configured remote branch.

## What Happens During `git pull`?

Conceptually:

```text
Remote Repository
       |
       | git fetch
       ↓
Remote-tracking branch
       |
       | merge/rebase
       ↓
Current Local Branch
```

By default, `git pull` performs a fetch followed by an integration step.

Depending on the repository configuration, that integration may use a merge or rebase.

## `git pull` vs `git fetch`

### `git pull`

Downloads remote changes and integrates them into the current branch.

```bash
git pull
```

### `git fetch`

Downloads information and commits from the remote repository without changing your current working branch.

```bash
git fetch
```

You can then inspect the changes before deciding how to integrate them.

## Example

Suppose someone has pushed new commits to GitHub:

```text
GitHub
origin/main
    |
    | New commits
    ↓
```

Your local repository does not have those commits yet.

Running:

```bash
git pull origin main
```

downloads the changes and integrates them into your local `main` branch.

## Pull Conflicts

A pull can result in a merge conflict if local and remote changes cannot be automatically combined.

Check the repository status:

```bash
git status
```

Resolve the conflicting files, stage the resolved files:

```bash
git add .
```

Then complete the merge if required:

```bash
git commit
```

## Important Points

- `git pull` downloads and integrates changes from a remote repository.
- `git pull origin main` pulls changes from the remote `main` branch.
- `git pull` usually performs a `git fetch` followed by an integration operation.
- The current branch determines where the pulled changes are integrated.
- Pulling can result in merge conflicts.
- `git fetch` is safer when you want to inspect remote changes before integrating them.

## Interview Questions

### What is the purpose of `git pull`?

`git pull` downloads changes from a remote repository and integrates them into the current local branch.

### What is the difference between `git pull` and `git fetch`?

`git pull` downloads remote changes and integrates them into the current branch, while `git fetch` downloads the remote changes without modifying the current working branch.

### What does `git pull origin feature1` mean?

It fetches changes from the `feature1` branch of the remote repository named `origin` and integrates them into the currently checked-out local branch.
