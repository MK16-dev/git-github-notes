# Remote Branches

## Overview

Git branches can exist locally on your computer or remotely on a repository such as GitHub.

Git provides commands to view and manage these branches.

## View Local Branches

To view branches that exist in the local repository:

```bash
git branch
```

Example:

```text
* main
  feature1
  feature2
```

The `*` indicates the branch currently checked out.

## View Remote Branches

To view branches that exist on the remote repository:

```bash
git branch -r
```

Example:

```text
origin/main
origin/feature1
origin/feature2
```

Here, `origin` represents the remote repository.

## View All Branches

To view both local and remote branches:

```bash
git branch -a
```

Example:

```text
* main
  feature1
  remotes/origin/main
  remotes/origin/feature1
```

This combines the local and remote branch information.

## Local vs Remote Branches

```text
Local Repository              Remote Repository
       │                             │
       │                             │
     main                         origin/main
   feature1                      origin/feature1
   feature2                      origin/feature2
```

A local branch and a remote-tracking branch are related, but they are not the same branch.

For example:

```text
feature1
```

is a local branch, while:

```text
origin/feature1
```

is a remote-tracking branch representing the branch on the remote repository.

## Push a Local Branch

To upload a local branch to the remote repository:

```bash
git push origin feature1
```

After pushing, the remote repository can contain:

```text
origin/feature1
```

You can then verify it using:

```bash
git branch -r
```

## Set Upstream Tracking

A common way to push a new branch and establish its upstream relationship is:

```bash
git push -u origin feature1
```

The `-u` option sets the remote branch as the upstream branch for the local branch.

After this has been configured, future pushes can usually be performed with:

```bash
git push
```

## Important Points

- `git branch` displays local branches.
- `git branch -r` displays remote-tracking branches.
- `git branch -a` displays both local and remote-tracking branches.
- `origin` is commonly used as the name of the main remote repository.
- `git push origin feature1` pushes a local branch to the remote repository.
- `git push -u origin feature1` pushes the branch and establishes upstream tracking.

## Interview Question

### What is the difference between `git branch`, `git branch -r`, and `git branch -a`?

- `git branch` → Shows local branches.
- `git branch -r` → Shows remote-tracking branches.
- `git branch -a` → Shows both local and remote-tracking branches.
