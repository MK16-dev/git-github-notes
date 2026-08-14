# Git Merge vs Rebase

## Overview

`git merge` and `git rebase` are both used to integrate changes from one branch into another.

The main difference is how they handle the project's commit history.

- `git merge` preserves the existing branch history and may create a merge commit.
- `git rebase` moves or replays commits onto a new base to create a more linear history.

## Git Merge

`git merge` combines the histories of two branches.

Example:

```bash
git checkout main
git merge feature1
```

If the branches have diverged, Git may create a merge commit.

Before merging:

```text
      C---D feature1
     /
A---B---E main
```

After merging:

```text
      C---D
     /     \
A---B---E---M main
```

`M` represents the merge commit.

## Git Rebase

`git rebase` moves the commits of one branch and reapplies them on top of another branch.

Example:

```bash
git checkout feature1
git rebase main
```

Before rebase:

```text
      C---D feature1
     /
A---B---E main
```

After rebase:

```text
A---B---E---C'---D' feature1
```

The commits are replayed on top of the latest `main` commit.

The rebased commits have new commit hashes.

## Comparison

| Feature | `git merge` | `git rebase` |
|---|---|---|
| Preserves branch history | Yes | Rewrites part of history |
| Creates merge commit | Sometimes | No |
| Produces linear history | Not always | Usually |
| Changes existing commit hashes | No | Yes |
| Suitable for shared branches | Generally safer | Requires caution |

## Merge Workflow

A typical merge workflow:

```bash
git checkout main
git pull
git merge feature1
git push origin main
```

This integrates the feature branch into `main`.

## Rebase Workflow

A typical rebase workflow:

```bash
git checkout feature1
git fetch origin
git rebase origin/main
```

After resolving any conflicts, continue the rebase:

```bash
git add .
git rebase --continue
```

If you need to cancel the rebase:

```bash
git rebase --abort
```

## Rebase and Remote Branches

Because rebase can rewrite commit history, pushing a rebased branch that has already been pushed may require:

```bash
git push --force-with-lease
```

`--force-with-lease` is safer than `--force` because Git checks that the remote branch has not changed unexpectedly.

Avoid rebasing commits that other developers are already depending on unless the team workflow explicitly allows it.

## When to Use Merge

Merge is commonly preferred when:

- You want to preserve the complete branch history.
- The branch is shared with other developers.
- You want a straightforward and safer integration method.
- Rewriting existing history would cause problems.

## When to Use Rebase

Rebase can be useful when:

- You want a cleaner, linear history.
- You are working on your own feature branch.
- You want to update your feature branch with the latest changes from `main`.
- Your team follows a rebase-based workflow.

## Important Points

- Both merge and rebase integrate changes from different branches.
- Merge preserves the existing history.
- Rebase rewrites commit history by replaying commits.
- Rebasing changes commit hashes.
- Avoid rebasing shared branches unless you understand the consequences.
- Prefer `git push --force-with-lease` over `git push --force` when a rebased remote branch must be updated.

## Interview Question

### What is the difference between `git merge` and `git rebase`?

`git merge` combines branches while preserving their existing history and may create a merge commit. `git rebase` rewrites the branch history by replaying its commits on top of another branch, producing a more linear history.

### Which is safer for a shared branch?

`git merge` is generally safer for shared branches because it does not rewrite existing commit history.

### Does rebase change commit hashes?

Yes. Because rebase creates new versions of the replayed commits, their commit hashes change.
