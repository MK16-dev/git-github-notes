# git merge

## Overview

`git merge` is used to combine the changes from one branch into another branch.

A common workflow is to develop a feature on a separate branch and then merge that branch into `main`.

## Basic Syntax

```bash
git merge <branch-name>
```

The branch specified in the command is merged into the **currently checked-out branch**.

## Example

Suppose the repository has:

```text
main
feature2
```

If the changes are completed on `feature2`, first switch to `main`:

```bash
git checkout main
```

Then merge `feature2` into `main`:

```bash
git merge feature2
```

The changes from `feature2` are now integrated into `main`.

## Typical Feature Branch Workflow

```bash
git checkout -b feature2
```

Create and switch to the feature branch.

Make changes to the project, then stage them:

```bash
git add .
```

Commit the changes:

```bash
git commit -m "Add feature2 changes"
```

Switch back to `main`:

```bash
git checkout main
```

Merge the feature branch:

```bash
git merge feature2
```

Push the updated `main` branch to GitHub:

```bash
git push origin main
```

After the merge, the feature branch can be deleted if it is no longer needed:

```bash
git branch -d feature2
```

## Fast-Forward Merge

A **Fast-forward merge** occurs when the target branch has not received any new commits since the feature branch was created.

For example:

```text
A---B                 main
     \
      C---D           feature2
```

After:

```bash
git checkout main
git merge feature2
```

Git can move the `main` branch pointer forward:

```text
A---B---C---D         main
            ↑
          feature2
```

No separate merge commit is required.

Git may display:

```text
Fast-forward
```

## Merge Commit

If both branches have developed independently, Git may need to create a merge commit.

Before merging:

```text
      C---D           feature2
     /
A---B---E             main
```

After merging:

```text
      C---D
     /     \
A---B---E---M         main
```

`M` represents the merge commit.

## Merge Conflicts

A merge conflict can occur when Git cannot automatically combine changes from two branches.

For example, if the same part of a file was changed differently on both branches, Git may mark the file as conflicted.

Check the conflict using:

```bash
git status
```

Git may mark the file as:

```text
both modified
```

After manually resolving the conflict:

```bash
git add <resolved-file>
```

Then complete the merge:

```bash
git commit
```

## Abort a Merge

If a merge conflict occurs and you want to cancel the merge:

```bash
git merge --abort
```

This attempts to return the repository to the state it was in before the merge started.

## Complete Branch Workflow

A common feature development workflow is:

```text
main
  |
  | git checkout -b feature2
  ↓
feature2
  |
  | Make changes
  | git add .
  | git commit
  ↓
feature2
  |
  | git checkout main
  ↓
main
  |
  | git merge feature2
  ↓
main + feature2 changes
  |
  | git push origin main
  ↓
GitHub
```

## Important Points

- `git merge` combines changes from one branch into the current branch.
- The branch being merged is specified in the command.
- Always switch to the branch that should receive the changes before running `git merge`.
- A Fast-forward merge can occur when the target branch has no new commits since the feature branch was created.
- A merge commit may be created when branches have diverged.
- Merge conflicts must be resolved manually when Git cannot combine changes automatically.
- `git merge --abort` can be used to cancel an ongoing merge.

## Interview Questions

### What does `git merge feature2` do?

It combines the changes from the `feature2` branch into the branch that is currently checked out.

### What is a Fast-forward merge?

A Fast-forward merge occurs when Git can move the target branch pointer forward to the latest commit without creating a separate merge commit.

### What is a merge conflict?

A merge conflict occurs when Git cannot automatically combine changes from different branches, usually because conflicting changes were made to the same part of a file.
