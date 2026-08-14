# git push

## Overview

`git push` is used to upload local commits to a remote repository such as GitHub.

It allows your local changes to become available on the remote repository.

## Basic Syntax

```bash
git push <remote> <branch>
```

Example:

```bash
git push origin main
```

Here:

- `git push` uploads commits.
- `origin` identifies the remote repository.
- `main` identifies the branch being pushed.

## Push a New Branch

To push a local feature branch to GitHub:

```bash
git push origin feature1
```

For a new branch, it is commonly recommended to establish upstream tracking:

```bash
git push -u origin feature1
```

After the upstream relationship is established, you can usually use:

```bash
git push
```

## What Does `-u` Mean?

The `-u` option sets the remote branch as the upstream branch for the current local branch.

For example:

```bash
git push -u origin feature1
```

creates the relationship:

```text
local feature1
       ↕
origin/feature1
```

After this, Git knows where the branch should push by default.

## Push the Main Branch

To push the local `main` branch:

```bash
git push origin main
```

If upstream tracking has already been configured:

```bash
git push
```

## Typical Workflow

Make changes to a project:

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
       ↓
git push
       ↓
Remote Repository
```

Example:

```bash
git add .
git commit -m "Update project"
git push origin main
```

## Push a Feature Branch

A common feature workflow is:

```bash
git switch -c feature-login
```

Make changes and commit them:

```bash
git add .
git commit -m "Add login feature"
```

Push the feature branch:

```bash
git push -u origin feature-login
```

The branch is now available on GitHub and can be used to create a Pull Request.

## Push vs Commit

`git commit` and `git push` perform different operations.

### `git commit`

Saves changes to the local Git repository:

```bash
git commit -m "Add login feature"
```

### `git push`

Uploads committed changes to the remote repository:

```bash
git push origin main
```

The relationship is:

```text
git commit
    ↓
Local Repository
    ↓
git push
    ↓
Remote Repository
```

## Push vs Pull

| Command | Direction | Purpose |
|---|---|---|
| `git push` | Local → Remote | Upload local commits |
| `git pull` | Remote → Local | Download and integrate remote changes |
| `git fetch` | Remote → Local | Download remote information without integrating |

## Push Rejected

Sometimes a push may be rejected because the remote branch contains commits that are not present locally.

For example:

```text
! [rejected] main -> main
```

In this situation, you may first need to update your local branch:

```bash
git pull origin main
```

Then resolve any conflicts if necessary, commit the result, and push again:

```bash
git push origin main
```

## Force Push

A force push can overwrite remote history:

```bash
git push --force
```

This should be used with extreme caution because it can remove commits from the remote branch.

When a force push is genuinely required, a safer option is:

```bash
git push --force-with-lease
```

This performs an additional check before updating the remote branch.

Avoid force-pushing shared branches unless your team workflow explicitly requires it.

## Verify the Remote Branch

After pushing, you can view remote-tracking branches:

```bash
git branch -r
```

Or view all branches:

```bash
git branch -a
```

You can also verify the remote URL:

```bash
git remote -v
```

## Important Points

- `git push` uploads local commits to a remote repository.
- `git push origin main` pushes the local `main` branch to `origin`.
- `git push -u origin feature1` pushes a new branch and establishes upstream tracking.
- `git commit` saves changes locally; `git push` uploads those commits remotely.
- A push can be rejected when the remote contains changes that your local branch does not have.
- Avoid using `git push --force` on shared branches.
- `git push --force-with-lease` is safer when a force push is necessary.

## Interview Questions

### What does `git push` do?

`git push` uploads local commits to a remote repository.

### What is the purpose of `-u`?

It establishes an upstream relationship between the local branch and its remote branch.

### What is the difference between `git commit` and `git push`?

`git commit` saves changes in the local repository, while `git push` uploads those committed changes to a remote repository.

### Why might `git push` be rejected?

A push may be rejected when the remote branch contains commits that the local branch does not have. The local branch usually needs to be updated before pushing again.
