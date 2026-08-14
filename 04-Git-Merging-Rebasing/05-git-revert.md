# git revert

## Overview

`git revert` is used to undo the changes introduced by a specific commit.

Instead of deleting or rewriting the existing commit history, `git revert` creates a **new commit** that reverses the changes made by the selected commit.

This makes `git revert` a safer option when the commit has already been pushed to a shared remote repository.

## Basic Syntax

```bash
git revert <commit-hash>
```

Example:

```bash
git revert a1b2c3d
```

Git creates a new commit that reverses the changes introduced by `a1b2c3d`.

## How It Works

Suppose the history is:

```text
A---B---C---D
```

If commit `C` introduced an unwanted change:

```bash
git revert C
```

Git creates a new commit:

```text
A---B---C---D---C'
```

`C'` reverses the changes introduced by `C`.

The original commit `C` is still part of the history.

## Revert vs Reset

These commands undo changes in different ways.

### `git reset`

```bash
git reset --hard HEAD~1
```

Moves the branch pointer backward and can rewrite history.

### `git revert`

```bash
git revert <commit-hash>
```

Creates a new commit that reverses an earlier commit.

| Feature | `git reset` | `git revert` |
|---|---|---|
| Rewrites history | Can | No |
| Creates a new commit | No | Yes |
| Safer for shared branches | Generally no | Generally yes |
| Original commit remains in history | No longer part of current branch history | Yes |

## Find the Commit to Revert

Use:

```bash
git log --oneline
```

Example:

```text
d4e5f6a Add payment feature
a1b2c3d Add login feature
789abcd Initial commit
```

If you want to undo the login feature:

```bash
git revert a1b2c3d
```

## Revert the Latest Commit

To revert the most recent commit:

```bash
git revert HEAD
```

Git will create a new commit that reverses the latest commit.

## Revert Multiple Commits

Multiple commits can also be reverted.

For example:

```bash
git revert <commit1> <commit2>
```

Each selected commit is reverted.

When reverting multiple commits, understand the order and dependencies between the changes to avoid conflicts.

## Revert Conflicts

A revert can result in a conflict if later changes depend on the changes being reverted.

Check the status:

```bash
git status
```

Resolve the conflicting files manually.

Then stage the resolved files:

```bash
git add .
```

Continue the revert:

```bash
git revert --continue
```

## Abort a Revert

If you want to cancel an ongoing revert:

```bash
git revert --abort
```

This attempts to return the repository to the state it was in before the revert started.

## Push a Revert

After the revert creates a new commit, it can be pushed normally:

```bash
git push origin main
```

This is one reason `git revert` is commonly used when undoing changes that have already been pushed to a shared repository.

## Practical Example

Suppose a faulty commit was pushed to GitHub:

```text
main
 |
 A---B---C
         ↑
      faulty commit
```

Instead of resetting the shared branch:

```bash
git reset --hard B
```

you can safely create a reversing commit:

```bash
git revert C
```

The history becomes:

```text
A---B---C---C'
```

Then push it:

```bash
git push origin main
```

The faulty changes are undone while the history remains intact.

## Important Points

- `git revert` creates a new commit that reverses an earlier commit.
- It does not remove the original commit from history.
- It is generally safer than reset for already-pushed commits.
- `git revert HEAD` reverts the latest commit.
- `git revert --continue` continues a revert after resolving conflicts.
- `git revert --abort` cancels an ongoing revert.
- After reverting, the new commit can be pushed normally.

## Interview Questions

### What is `git revert`?

`git revert` creates a new commit that reverses the changes introduced by an earlier commit.

### Why is `git revert` safer than `git reset` for shared branches?

`git revert` does not rewrite existing commit history. Instead, it adds a new commit that reverses the previous changes.

### Does `git revert` delete the original commit?

No. The original commit remains in the Git history.

### How do you revert the latest commit?

```bash
git revert HEAD
```
