# git reflog

## Overview

`git reflog` records changes to the tips of local branches and other local references.

It is especially useful when you accidentally reset, rebase, or move a branch and need to find a previous state.

Unlike `git log`, which shows commit history, `git reflog` shows how references such as `HEAD` have moved.

## View the Reflog

To view the reflog:

```bash
git reflog
```

Example:

```text
2afe927 HEAD@{0}: checkout: moving from feature1 to master
2afe927 HEAD@{1}: commit: Add feature1
2b6a33b HEAD@{2}: checkout: moving from master to feature1
2b6a33b HEAD@{3}: commit: Add README file
```

Each entry has a reference such as:

```text
HEAD@{0}
HEAD@{1}
HEAD@{2}
```

`HEAD@{0}` represents the current position, while older entries represent previous positions of `HEAD`.

## Reflog vs Git Log

These commands provide different information.

### `git log`

Shows the commit history reachable from the current branch.

```bash
git log --oneline
```

### `git reflog`

Shows movements of `HEAD` and local references.

```bash
git reflog
```

A simplified comparison:

```text
git log
   ↓
Commit history

git reflog
   ↓
History of reference movements
```

## Reflog After Reset

Suppose a commit is accidentally removed from the current branch using:

```bash
git reset --hard HEAD~1
```

The commit may no longer appear in the normal branch history.

However, the previous `HEAD` position may still be available through:

```bash
git reflog
```

Example:

```text
abc1234 HEAD@{0}: reset: moving to HEAD~1
def5678 HEAD@{1}: commit: Important changes
```

The previous commit can then be identified using its hash:

```text
def5678
```

## Recovering a Previous State

If a previous commit is found in the reflog, it can be inspected:

```bash
git show def5678
```

A branch can also be moved back to that commit if recovery is required.

For example:

```bash
git reset --hard def5678
```

Use commands such as `reset --hard` carefully because they can modify or discard working-directory changes.

## Reflog Is Local

Reflog information is stored locally.

It is not normally pushed to GitHub along with the repository.

Therefore:

```text
Local Repository
      |
      └── Reflog
```

is different from:

```text
GitHub Repository
      |
      └── Remote Commit History
```

## Common Uses

`git reflog` can help when:

- A commit appears to have disappeared.
- A branch was accidentally reset.
- A rebase caused unexpected history changes.
- `HEAD` was moved to the wrong commit.
- You need to find a previous position of a branch.
- You want to recover a previous state of your local repository.

## Important Points

- `git reflog` records movements of local references.
- It can help recover commits that are no longer reachable from a branch.
- `git log` shows commit history, while `git reflog` shows reference movements.
- Reflog information is local.
- Reflog is particularly useful after operations such as `reset` and `rebase`.
- A reflog entry can be used to locate the commit hash of a previous state.

## Interview Questions

### What is `git reflog`?

`git reflog` records changes to local references such as `HEAD` and helps identify previous states of a repository.

### What is the difference between `git log` and `git reflog`?

`git log` shows commit history reachable from a branch, while `git reflog` records movements of local references such as `HEAD`.

### Can reflog help recover a deleted commit?

Yes. If the commit is still referenced in the local reflog, its commit hash can be found and used to recover or inspect it.

### Is reflog available on GitHub?

Reflog is a local Git feature. It is not part of the normal remote repository history shown on GitHub.
