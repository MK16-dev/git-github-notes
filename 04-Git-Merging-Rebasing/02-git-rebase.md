# git rebase

## Overview

`git rebase` is used to move or replay commits from one branch onto another base branch.

It is commonly used to update a feature branch with the latest changes from `main` while maintaining a linear commit history.

## Basic Syntax

```bash
git rebase <base-branch>
```

Example:

```bash
git checkout feature1
git rebase main
```

This takes the commits from `feature1` and replays them on top of the latest commit on `main`.

## Example

Before rebase:

```text
      C---D feature1
     /
A---B---E main
```

Run:

```bash
git checkout feature1
git rebase main
```

After rebase:

```text
A---B---E---C'---D' feature1
```

The commits `C` and `D` are replayed as `C'` and `D'`.

Because new commits are created, their commit hashes are different.

## Updating a Feature Branch

Suppose `main` has received new changes while you are working on `feature1`.

You can update your feature branch using:

```bash
git checkout feature1
git fetch origin
git rebase origin/main
```

This replays your feature commits on top of the latest remote `main`.

## Rebase Conflicts

A conflict can occur when Git cannot automatically apply a commit during the rebase.

Check the status:

```bash
git status
```

Git will identify the files containing conflicts.

Open the conflicted files and resolve the changes manually.

Then stage the resolved files:

```bash
git add .
```

Continue the rebase:

```bash
git rebase --continue
```

Git may stop again if another conflict is encountered. Resolve it, stage the changes, and run:

```bash
git rebase --continue
```

Repeat until the rebase is complete.

## Abort a Rebase

If you want to cancel the rebase and return to the state before the rebase started:

```bash
git rebase --abort
```

This is useful when the conflicts are difficult to resolve or you decide not to continue with the rebase.

## Skip a Commit

If a particular commit should not be applied during the rebase:

```bash
git rebase --skip
```

Use this only when you understand why the commit should be skipped.

## Interactive Rebase

Interactive rebase allows you to modify a series of commits.

Basic syntax:

```bash
git rebase -i HEAD~3
```

This opens an editor where you can choose actions for the last three commits.

Common actions include:

```text
pick    → Keep the commit
reword  → Change the commit message
edit    → Stop and modify the commit
squash  → Combine the commit with the previous commit
fixup   → Combine commits and discard the later commit message
drop    → Remove the commit
```

Interactive rebase is useful for cleaning up your own local commit history before sharing it.

## Rebase vs Merge

```text
Merge:

A---B---E
     \   \
      C---D---M

Rebase:

A---B---E---C'---D'
```

Merge preserves the original branch structure.

Rebase creates a more linear history by replaying commits.

## Important Warning

Rebase rewrites commit history.

Because the commits are recreated, their commit hashes change.

Avoid rebasing commits that other developers are already working on unless your team has agreed to do so.

For your own feature branch, rebasing can be useful before merging it into `main`.

## Pushing a Rebasing Branch

If a branch was already pushed to a remote repository and then rebased, a normal push may be rejected because the commit history has changed.

In such cases:

```bash
git push --force-with-lease
```

`--force-with-lease` is preferred over:

```bash
git push --force
```

because it provides an additional safety check before overwriting the remote branch.

## Practical Workflow

A common workflow for updating a feature branch is:

```bash
git checkout feature1
```

Fetch the latest remote information:

```bash
git fetch origin
```

Rebase the feature branch onto the latest main:

```bash
git rebase origin/main
```

If conflicts occur:

```bash
git status
```

Resolve the conflicts, then:

```bash
git add .
git rebase --continue
```

If you need to cancel:

```bash
git rebase --abort
```

After a successful rebase, if the branch was already pushed:

```bash
git push --force-with-lease
```

## Important Points

- `git rebase` replays commits onto a new base.
- Rebase creates new commit hashes.
- Rebase can produce a cleaner, linear history.
- `git rebase --continue` continues a rebase after resolving conflicts.
- `git rebase --abort` cancels an ongoing rebase.
- `git rebase --skip` skips the current commit.
- Interactive rebase can be used to clean up local commit history.
- Avoid rebasing shared branches unless the workflow allows it.
- Use `git push --force-with-lease` instead of `git push --force` when a rebased branch needs to be pushed.

## Interview Questions

### What does `git rebase` do?

It moves or replays commits from one branch onto another base commit, creating a more linear project history.

### What happens to commit hashes during rebase?

The replayed commits receive new commit hashes because new commits are created.

### How do you continue a rebase after resolving a conflict?

```bash
git add .
git rebase --continue
```

### How do you cancel a rebase?

```bash
git rebase --abort
```

### Why should you avoid rebasing shared branches?

Because rebase rewrites commit history and changes commit hashes, which can cause problems for other developers who already have the original history.
