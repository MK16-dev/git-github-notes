# git init

## Overview

`git init` initializes a new Git repository in the current directory. It creates a `.git` directory that contains the metadata required by Git to track the project.

## Syntax

```bash
git init
```

## How It Works

When `git init` is executed inside a project directory, Git creates a hidden `.git` directory.

```text
project/
├── .git/
├── src/
├── README.md
└── ...
```

The `.git` directory stores information required by Git, including commits, branches, references, and repository configuration.

## Example

```bash
mkdir my-project
cd my-project
git init
```

## Important Points

- `git init` creates a local Git repository.
- It creates a hidden `.git` directory.
- It does not create a repository on GitHub.
- It does not automatically commit files.
- Files must be added using `git add`.
- The `.git` directory contains important repository information.

## Typical Workflow

```bash
git init
git status
git add .
git commit -m "Initial commit"
```

## `git init` vs GitHub

`git init` creates a Git repository locally on your computer.

A GitHub repository is a remote repository hosted on GitHub.

The local repository can later be connected to GitHub using:

```bash
git remote add origin <repository-url>
```

Then changes can be uploaded using:

```bash
git push
```

## Interview Question

### What is the purpose of `git init`?

`git init` initializes a new Git repository in the current directory by creating a `.git` directory that stores Git's metadata and repository information.
