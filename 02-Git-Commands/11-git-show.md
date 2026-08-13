# git show

## Overview

`git show` is used to display detailed information about a specific Git object, most commonly a commit.

For a commit, it shows the commit metadata and the changes introduced by that commit.

## Syntax

```bash
git show <commit-hash>
```

## View the Latest Commit

To view details of the most recent commit:

```bash
git show
```

Git displays information such as:

- Commit hash
- Author
- Date
- Commit message
- Changes introduced by the commit

## Example

First, view the commit history:

```bash
git log --oneline
```

Example:

```text
8f3a2c1 Add Git command notes
4d7b91e Add Git basics
```

Then use the commit hash with `git show`:

```bash
git show 8f3a2c1
```

This displays the details and changes associated with that commit.

## View a Specific File from a Commit

To view how a specific file looked in a particular commit:

```bash
git show <commit-hash>:<file-path>
```

Example:

```bash
git show 8f3a2c1:README.md
```

## View a Commit Summary

To display a shorter summary of the changes:

```bash
git show --stat <commit-hash>
```

This shows the files changed and the number of lines added or removed without displaying the complete changes.

## View Only the Commit Information

To view the commit information without the changes:

```bash
git show --no-patch <commit-hash>
```

## `git show` vs `git log`

| Command | Purpose |
|---|---|
| `git log` | Displays commit history |
| `git show` | Displays detailed information about a specific commit |

## Important Points

- `git show` is commonly used to inspect a specific commit.
- It displays the commit metadata and changes introduced by the commit.
- `git show` without a commit hash displays the latest commit.
- A commit hash can be obtained using `git log`.

## Interview Question

### What is the purpose of `git show`?

`git show` is used to display detailed information about a Git object, most commonly a commit, including its metadata and the changes introduced by it.
