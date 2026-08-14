# Pushing Branches to a Remote Repository

## Overview

A local branch can be pushed to a remote repository such as GitHub.

Pushing a branch uploads its commits to the remote repository so that the branch can be accessed by other collaborators.

## Push a Branch

To push a local branch to the remote repository:

```bash
git push origin feature1
```

Here:

- `git push` uploads local commits to a remote repository.
- `origin` is the name of the remote repository.
- `feature1` is the branch being pushed.

## Set Upstream Tracking

For a new branch, it is common to use:

```bash
git push -u origin feature1
```

The `-u` option establishes an upstream relationship between the local branch and the remote branch.

After the upstream branch has been configured, future pushes can usually be performed using:

```bash
git push
```

## Example Workflow

Create a feature branch:

```bash
git checkout -b feature1
```

Make changes to the project.

Stage the changes:

```bash
git add .
```

Create a commit:

```bash
git commit -m "Add feature1"
```

Push the branch to GitHub:

```bash
git push -u origin feature1
```

The branch will now be available on the remote repository.

## Verify the Remote Branch

After pushing, use:

```bash
git branch -r
```

You may see:

```text
origin/main
origin/feature1
```

To view both local and remote branches:

```bash
git branch -a
```

## GitHub Pull Request

After a feature branch is pushed to GitHub, GitHub may provide an option to create a **Pull Request (PR)**.

A Pull Request is used to propose merging changes from one branch into another, commonly:

```text
feature1 → main
```

A Pull Request allows changes to be reviewed before they are merged into the main branch.

Typical workflow:

```text
Local feature branch
        |
        | git push
        ↓
Remote feature branch
        |
        | Pull Request
        ↓
Review
        |
        | Merge
        ↓
main
```

## Push vs Pull Request

These are different operations.

### `git push`

Uploads local commits to a remote repository.

```bash
git push -u origin feature1
```

### Pull Request

A GitHub feature used to propose and review changes before merging branches.

A Pull Request is not created by `git push` itself. However, GitHub can display a link or prompt to create one after a new branch is pushed.

## Important Points

- `git push` uploads local commits to a remote repository.
- `git push origin feature1` pushes the `feature1` branch.
- `git push -u origin feature1` also establishes upstream tracking.
- A pushed branch can be used to create a Pull Request on GitHub.
- A Pull Request is a collaboration and review mechanism, not a Git command.

## Interview Question

### What does `git push origin feature1` do?

It uploads the local `feature1` branch and its commits to the remote repository named `origin`.

### What is the purpose of `-u` in `git push -u origin feature1`?

The `-u` option establishes the remote `origin/feature1` branch as the upstream branch for the local `feature1` branch, making future `git push` and `git pull` commands simpler.
