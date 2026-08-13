# git add

## Overview

`git add` is used to add changes from the working directory to the staging area.

The staging area allows you to select which changes will be included in the next commit.

## Syntax

```bash
git add <file-name>
```

## Add a Specific File

To stage a single file:

```bash
git add README.md
```

## Add Multiple Files

To stage multiple specific files:

```bash
git add file1.txt file2.txt
```

## Add All Changes

To stage all new, modified, and deleted files in the current directory:

```bash
git add .
```

## How It Works

The basic Git workflow is:

```text
Working Directory
       |
       | git add
       ↓
Staging Area
       |
       | git commit
       ↓
Local Repository
```

`git add` does not create a commit. It only prepares the selected changes for the next commit.

## Example

Suppose the project contains:

```text
project/
├── README.md
├── index.html
└── style.css
```

If only `README.md` was modified, use:

```bash
git add README.md
```

If all changes should be staged:

```bash
git add .
```

Then check the staging area:

```bash
git status
```

The staged files will appear under:

```text
Changes to be committed:
```

## Removing a File from the Staging Area

If a file was staged accidentally, it can be removed from the staging area using:

```bash
git restore --staged <file-name>
```

Example:

```bash
git restore --staged README.md
```

This removes the file from the staging area without deleting the changes from the working directory.

## Important Points

- `git add` moves changes to the staging area.
- It does not create a commit.
- `git add <file-name>` stages a specific file.
- `git add .` stages all changes in the current directory.
- `git status` can be used to verify which files are staged.

## Interview Question

### What is the purpose of `git add`?

`git add` moves selected changes from the working directory to the staging area, preparing them to be included in the next commit.
