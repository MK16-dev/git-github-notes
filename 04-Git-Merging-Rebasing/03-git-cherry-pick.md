# git cherry-pick

## Overview

`git cherry-pick` is used to apply the changes introduced by a specific commit onto the current branch.

Unlike `git merge`, which combines an entire branch, cherry-pick allows you to select individual commits.

## Basic Syntax

```bash
git cherry-pick <commit-hash>
```

Example:

```bash
git cherry-pick a1b2c3d
```

The commit identified by `a1b2c3d` is applied to the current branch.

## How It Works

Suppose the repository looks like this:

```text
A---B---C---D        main
     \
      E---F          feature1
```

Suppose commit `E` contains a useful change that you want on `main`, but you don't want to merge the entire `feature1` branch.

First switch to `main`:

```bash
git checkout main
```

Then cherry-pick commit `E`:

```bash
git cherry-pick <commit-hash-of-E>
```

The result will look similar to:

```text
A---B---C---D---E'   main
     \
      E---F          feature1
```

`E'` is a new commit containing the changes from `E`.

## Find a Commit Hash

Use:

```bash
git log --oneline
```

Example:

```text
a1b2c3d Add login validation
e4f5g6h Update homepage
i7j8k9l Add navbar
```

You can then select the required commit:

```bash
git cherry-pick a1b2c3d
```

## Cherry-Pick Multiple Commits

To cherry-pick multiple individual commits:

```bash
git cherry-pick <commit1> <commit2>
```

Example:

```bash
git cherry-pick a1b2c3d e4f5g6h
```

## Cherry-Pick a Range of Commits

A range can also be cherry-picked:

```bash
git cherry-pick A^..D
```

This applies the commits from `A` through `D`.

## Cherry-Pick Conflicts

A conflict can occur if the selected commit cannot be applied cleanly to the current branch.

Check the status:

```bash
git status
```

Resolve the conflicting files manually.

Then stage the resolved files:

```bash
git add .
```

Continue the cherry-pick:

```bash
git cherry-pick --continue
```

## Abort Cherry-Pick

If you want to cancel the cherry-pick:

```bash
git cherry-pick --abort
```

This returns the repository to the state it was in before the cherry-pick started.

## Cherry-Pick vs Merge

| Feature | `git cherry-pick` | `git merge` |
|---|---|---|
| Selects individual commits | Yes | No |
| Combines entire branch history | No | Yes |
| Creates a new commit | Yes | Sometimes |
| Useful for applying a specific fix | Yes | Not usually |

## Example Use Case

Suppose a bug was fixed on a development branch:

```text
main
  |
  └── development
        |
        └── Fix critical bug
```

You need that specific fix on `main`, but the rest of the development branch is not ready.

You can:

```bash
git checkout main
git cherry-pick <bug-fix-commit>
```

This applies only the bug-fix commit to `main`.

## Important Points

- `git cherry-pick` applies a specific commit to the current branch.
- It is useful when you need one particular change without merging an entire branch.
- Cherry-picking creates a new commit on the current branch.
- The new commit has a different commit hash.
- Conflicts can occur during cherry-picking.
- `git cherry-pick --continue` continues after resolving conflicts.
- `git cherry-pick --abort` cancels an ongoing cherry-pick.

## Interview Questions

### What is `git cherry-pick`?

`git cherry-pick` applies the changes introduced by a specific commit to the current branch.

### What is the difference between cherry-pick and merge?

Merge combines changes from an entire branch, while cherry-pick allows you to select and apply specific commits.

### How do you cancel a cherry-pick?

```bash
git cherry-pick --abort
```

### When would you use cherry-pick?

A common use case is applying a specific bug fix or feature commit from another branch without merging the entire branch.
