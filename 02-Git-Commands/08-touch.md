# touch

## Overview

`touch` is a command used to create a new empty file or update the timestamp of an existing file.

It is commonly used in Linux, Unix-based systems, and Git Bash.

## Syntax

```bash
touch <file-name>
```

## Create a New File

To create an empty file:

```bash
touch README.md
```

This creates:

```text
README.md
```

Multiple files can be created at once:

```bash
touch file1.txt file2.txt file3.txt
```

## Example with Git

A common Git workflow using `touch` is:

```bash
touch README.md
git status
git add README.md
git commit -m "Add README file"
```

Here, `touch` creates the file, while Git commands track and save the file in the repository.

## Important Points

- `touch` is not a Git command.
- It can create an empty file.
- It can create multiple files in a single command.
- It is commonly available in Git Bash.
- `git add` is required before a newly created file can be included in a commit.

## Interview Question

### Is `touch` a Git command?

No. `touch` is a Unix/Linux command used to create files or update file timestamps. It is commonly used with Git through terminals such as Git Bash.
