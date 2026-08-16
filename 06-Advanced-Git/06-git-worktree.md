# git worktree

## Overview

`git worktree` allows multiple working directories to be associated with a single Git repository.

It is useful when you need to work on multiple branches at the same time without repeatedly switching branches.

For example, you can have:

```text
project-main/      → main branch
project-feature/   → feature branch
```

Both working directories belong to the same Git repository.

## Why Use Git Worktrees?

Normally, switching branches changes the files in your working directory:

```bash
git switch main
git switch feature1
```

With worktrees, different branches can be checked out into different directories simultaneously.

This can be useful when:

- Working on multiple features at the same time.
- Comparing different branches.
- Testing a branch while keeping another branch available.
- Reviewing another branch without disturbing your current work.

## Create a Worktree

Basic syntax:

```bash
git worktree add <path> <branch>
```

Example:

```bash
git worktree add ../feature1-worktree feature1
```

This creates a new directory containing the `feature1` branch.

The structure may look like:

```text
git-github-notes/
feature1-worktree/
```

The main repository and worktree share the same Git repository data.

## Create a New Branch and Worktree

You can create a new branch and worktree together:

```bash
git worktree add -b feature2 ../feature2-worktree
```

This creates:

```text
feature2
```

and checks it out in:

```text
../feature2-worktree
```

## List Worktrees

To see all worktrees:

```bash
git worktree list
```

Example:

```text
C:/Projects/project        abc1234 [main]
C:/Projects/feature-work   def5678 [feature1]
```

This shows the paths, commits, and branches associated with the worktrees.

## Remove a Worktree

To remove a worktree:

```bash
git worktree remove ../feature1-worktree
```

This removes the worktree directory while keeping the main repository.

Make sure any important uncommitted changes in the worktree have been saved before removing it.

## Prune Worktree Information

If a worktree directory was manually deleted, Git may still have information about it.

Clean up stale worktree information with:

```bash
git worktree prune
```

## Worktree vs Branch Switching

### Traditional branch switching

```text
One directory
     |
     ├── main
     |
     └── feature1
```

You switch between branches:

```bash
git switch main
git switch feature1
```

### Worktrees

```text
Main directory
     ↓
    main

Feature directory
     ↓
   feature1
```

Both branches can be worked on at the same time.

## Example Workflow

Suppose you are currently working on `main`.

Create a worktree for a feature:

```bash
git worktree add ../feature1-worktree feature1
```

Move into it:

```bash
cd ../feature1-worktree
```

Now you can work on `feature1` without switching the branch in your original directory.

Return to the original repository:

```bash
cd ../git-github-notes
```

The original working directory can continue using its own branch.

## Important Points

- `git worktree` allows multiple working directories for one Git repository.
- Each worktree can have a different branch checked out.
- Worktrees are useful when working on multiple branches simultaneously.
- `git worktree list` displays existing worktrees.
- `git worktree remove` removes a worktree.
- `git worktree prune` removes stale worktree information.
- Worktrees share the same underlying Git repository data.

## Interview Questions

### What is `git worktree`?

`git worktree` allows multiple working directories to be connected to the same Git repository, making it possible to work on different branches simultaneously.

### Why would you use a worktree?

A worktree is useful when you need to work on multiple branches at the same time without repeatedly switching branches in the same directory.

### How do you list worktrees?

```bash
git worktree list
```

### How do you create a worktree?

```bash
git worktree add <path> <branch>
```

### How do you remove a worktree?

```bash
git worktree remove <path>
```
