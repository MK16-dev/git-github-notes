# git log

## Overview

`git log` displays the commit history of a Git repository.

It provides information about previous commits, including the commit ID, author, date, and commit message.

## Syntax

```bash
git log
```

## Example

```bash
git log
```

Example output:

```text
commit 8f3a2c1...
Author: Mitali
Date:   Thu Aug 13 22:30:00 2026 +0530

    Add Git command notes

commit 4d7b91e...
Author: Mitali
Date:   Thu Aug 13 21:45:00 2026 +0530

    Add Git basics
```

Each commit has a unique commit ID called a **commit hash**.

## View Compact Commit History

To display commits in a shorter format:

```bash
git log --oneline
```

Example:

```text
8f3a2c1 Add Git command notes
4d7b91e Add Git basics
```

This format is useful when you want to quickly review the commit history.

## View a Limited Number of Commits

To display a specific number of recent commits:

```bash
git log -n 3
```

This displays the three most recent commits.

You can replace `3` with any required number.

## View Commit History with Branch Information

```bash
git log --oneline --all
```

This displays commits from all branches in a compact format.

## View Commit Details

To view the changes introduced by a specific commit:

```bash
git show <commit-hash>
```

Example:

```bash
git show 8f3a2c1
```

## Useful Options

| Command | Purpose |
|---|---|
| `git log` | Display detailed commit history |
| `git log --oneline` | Display compact commit history |
| `git log -n 3` | Display the latest 3 commits |
| `git log --all` | Display commits from all branches |
| `git show <commit-hash>` | Display details of a specific commit |

## Important Points

- `git log` is used to inspect commit history.
- Every commit has a unique commit hash.
- Commit history helps track changes made to a project.
- `git log --oneline` provides a compact view of the history.
- `git show` can be used to inspect a specific commit.

## Interview Question

### What is the purpose of `git log`?

`git log` displays the commit history of a Git repository, including information such as commit hashes, authors, dates, and commit messages.
