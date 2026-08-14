# git reset

## Overview

`git reset` is used to move the current branch to a different commit and can also be used to unstage changes.

It is commonly used to undo local commits or remove files from the staging area.

Because some forms of `git reset` can rewrite commit history, it should be used carefully, especially on shared branches.

## Three Reset Modes

Git provides three main reset modes:

```text
--soft
--mixed
--hard
```

They differ in what happens to the staging area and working directory.

## git reset --soft

```bash
git reset --soft HEAD~1
```

This moves the current branch back by one commit while keeping the changes staged.

Example:

```text
Before:

A---B---C  main

After:

A---B      main
     \
      C changes remain staged
```

Useful when you want to undo a commit but keep its changes ready to commit again.

## git reset --mixed

```bash
git reset --mixed HEAD~1
```

This is the default reset mode.

It moves the branch back by one commit and unstages the changes, but keeps the changes in the working directory.

It is equivalent to:

```bash
git reset HEAD~1
```

Example:

```text
Before:

A---B---C  main

After:

A---B      main

Changes from C remain in the working directory,
but they are no longer staged.
```

## git reset --hard

```bash
git reset --hard HEAD~1
```

This moves the branch back by one commit and removes the changes from both the staging area and working directory.

This can permanently discard uncommitted changes.

Use it carefully.

## HEAD~1

The notation:

```bash
HEAD~1
```

means the commit immediately before the current commit.

For example:

```text
A---B---C
        ↑
       HEAD
```

Then:

```bash
git reset HEAD~1
```

moves `HEAD` from `C` back to `B`.

You can also use:

```bash
HEAD~2
```

to refer to two commits before the current commit.

## Unstage a File

`git reset` can also be used to remove a file from the staging area.

Example:

```bash
git reset HEAD file.txt
```

The file remains in the working directory, but it is no longer staged.

Modern Git also provides:

```bash
git restore --staged file.txt
```

for this purpose.

## Reset vs Restore

| Command | Purpose |
|---|---|
| `git reset` | Move branch history or unstage changes |
| `git restore` | Restore files or unstage changes |

## Reset vs Revert

`git reset` and `git revert` are different.

### Reset

```bash
git reset --hard HEAD~1
```

Moves the branch pointer backward and can rewrite local history.

### Revert

```bash
git revert <commit-hash>
```

Creates a new commit that reverses the changes from an earlier commit.

This makes `git revert` generally safer for commits that have already been pushed to a shared remote repository.

## Important Warning

Be especially careful with:

```bash
git reset --hard
```

It can remove uncommitted changes from the working directory.

Also avoid using history-rewriting commands such as reset on shared branches unless you understand the consequences and your team workflow allows it.

## Important Points

- `git reset` can move the current branch to another commit.
- `--soft` keeps changes staged.
- `--mixed` keeps changes but unstages them.
- `--hard` removes changes from the staging area and working directory.
- `git reset HEAD file.txt` can unstage a file.
- `HEAD~1` refers to the previous commit.
- Reset can rewrite history.
- Use extra caution with `git reset --hard`.

## Interview Questions

### What is `git reset` used for?

It can be used to move the current branch to another commit and to unstage changes.

### What is the difference between `--soft`, `--mixed`, and `--hard`?

- `--soft` → keeps changes staged.
- `--mixed` → keeps changes but unstages them.
- `--hard` → removes changes from the staging area and working directory.

### Which reset mode is the most dangerous?

`git reset --hard` because it can discard uncommitted changes.

### Should you use reset on a shared branch?

Generally, avoid rewriting shared history with reset. For already-pushed commits that need to be undone, `git revert` is usually safer.
