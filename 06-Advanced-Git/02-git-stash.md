# git stash

## Overview

`git stash` temporarily saves changes in the working directory and staging area without creating a commit.

It is useful when you are working on something but need to temporarily switch branches or work on another task.

Instead of committing unfinished work, you can stash it and restore it later.

## Basic Syntax

```bash
git stash
```

This temporarily saves your current changes and returns the working directory to a clean state.

## Check the Stash

To view all saved stashes:

```bash
git stash list
```

Example:

```text
stash@{0}: WIP on feature1
stash@{1}: WIP on main
```

Each stash receives a reference such as:

```text
stash@{0}
```

## Restore Stashed Changes

To restore the most recent stash without removing it from the stash list:

```bash
git stash apply
```

The changes are restored to your working directory.

The stash remains available in the stash list.

## Apply a Specific Stash

If you have multiple stashes:

```bash
git stash apply stash@{1}
```

This applies the specified stash.

## Restore and Remove a Stash

To restore the most recent stash and remove it from the stash list:

```bash
git stash pop
```

The difference is:

```text
git stash apply
    ↓
Restore changes
    ↓
Stash remains

git stash pop
    ↓
Restore changes
    ↓
Stash is removed
```

## Remove a Stash

To delete a specific stash:

```bash
git stash drop stash@{0}
```

To remove all stashes:

```bash
git stash clear
```

Use `git stash clear` carefully because all saved stashes will be removed.

## Stash With a Message

You can give a stash a meaningful description:

```bash
git stash push -m "Work on login feature"
```

Then:

```bash
git stash list
```

may show:

```text
stash@{0}: On feature1: Work on login feature
```

Meaningful stash messages make it easier to identify saved work.

## Stash Including Untracked Files

By default, `git stash` does not include untracked files.

To include untracked files:

```bash
git stash -u
```

or:

```bash
git stash --include-untracked
```

## Typical Workflow

Suppose you are working on a feature:

```text
feature1
   |
   | Uncommitted changes
   ↓
Need to switch branches
```

Instead of committing unfinished work:

```bash
git stash
```

Switch to another branch:

```bash
git checkout main
```

Work on the other task.

When you are ready to return:

```bash
git checkout feature1
```

Restore your changes:

```bash
git stash pop
```

Your unfinished work is restored.

## Stash Workflow

```text
Uncommitted Changes
        |
        ↓
   git stash
        |
        ↓
Clean Working Directory
        |
        ↓
Switch Branch / Work on Another Task
        |
        ↓
Return to Original Branch
        |
        ↓
   git stash pop
        |
        ↓
Changes Restored
```

## Important Points

- `git stash` temporarily saves uncommitted changes.
- It is useful when you need to switch branches without committing unfinished work.
- `git stash list` shows saved stashes.
- `git stash apply` restores changes but keeps the stash.
- `git stash pop` restores changes and removes the stash.
- `git stash drop` removes a specific stash.
- `git stash clear` removes all stashes.
- `git stash -u` includes untracked files.
- Giving stashes meaningful messages makes them easier to identify.

## Interview Questions

### What is `git stash`?

`git stash` temporarily saves uncommitted changes so that the working directory can be used for another task without creating a commit.

### What is the difference between `git stash apply` and `git stash pop`?

`git stash apply` restores the changes while keeping the stash. `git stash pop` restores the changes and removes the stash if the operation completes successfully.

### Does `git stash` include untracked files?

Not by default. Use:

```bash
git stash -u
```

to include untracked files.

### When would you use `git stash`?

A common use case is when you have unfinished changes but need to temporarily switch branches to work on another task.
