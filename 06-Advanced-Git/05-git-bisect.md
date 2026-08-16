# git bisect

## Overview

`git bisect` is used to find the commit that introduced a bug by performing a binary search through the project's commit history.

Instead of checking every commit one by one, Git repeatedly divides the commit history into smaller sections.

This makes it much faster to identify the commit that introduced a problem.

## Why Use git bisect?

Suppose a project has many commits:

```text
A---B---C---D---E---F---G---H
```

The project works correctly at commit `A`, but the bug exists at commit `H`.

Checking every commit manually would take time.

`git bisect` can test a middle commit, determine whether the bug exists there, and continue narrowing down the range.

```text
A---B---C---D---E---F---G---H
            ↑
         Test here
```

Git continues this process until the problematic commit is identified.

## Start Bisecting

Start a bisect session:

```bash
git bisect start
```

Mark the current commit as bad:

```bash
git bisect bad
```

Then identify a commit where the project was known to work correctly:

```bash
git bisect good <commit-hash>
```

Git will check out a commit in the middle of the range.

## Test the Current Commit

At each step, test the project.

If the bug exists:

```bash
git bisect bad
```

If the bug does not exist:

```bash
git bisect good
```

Git will select another commit to test.

Continue until Git identifies the first bad commit.

## Example Workflow

```bash
git bisect start
git bisect bad
git bisect good abc1234
```

Git checks out a commit to test.

If the bug exists:

```bash
git bisect bad
```

If the bug does not exist:

```bash
git bisect good
```

Repeat the process until Git identifies the problematic commit.

## End the Bisect Session

After finding the problematic commit:

```bash
git bisect reset
```

This ends the bisect session and returns to the branch state from before the bisect operation.

## Automated Bisect

If the project has an automated test that can determine whether a commit is good or bad, `git bisect` can run the test automatically.

Example:

```bash
git bisect run <test-command>
```

For example:

```bash
git bisect run npm test
```

Git uses the command's result to determine whether each commit is good or bad.

## Basic Workflow

```text
Start bisect
     ↓
Mark current commit as bad
     ↓
Mark known working commit as good
     ↓
Git selects a middle commit
     ↓
Test the commit
     ↓
 ┌───────────────┐
 │               │
Good            Bad
 │               │
 ↓               ↓
git bisect      git bisect
good            bad
 │               │
 └───────┬───────┘
         ↓
   Repeat testing
         ↓
First bad commit
         ↓
git bisect reset
```

## Important Points

- `git bisect` helps identify the commit that introduced a bug.
- It uses a binary-search approach.
- `git bisect good` marks a commit as working correctly.
- `git bisect bad` marks a commit as containing the bug.
- `git bisect reset` ends the bisect session.
- `git bisect run` can automate the process using a test command.
- It is especially useful in repositories with many commits.

## Interview Questions

### What is `git bisect`?

`git bisect` is a Git debugging tool that uses binary search to identify the commit that introduced a bug.

### Why is binary search useful in `git bisect`?

Instead of testing every commit, Git repeatedly divides the range of commits in half, significantly reducing the number of commits that need to be tested.

### What does `git bisect good` mean?

It tells Git that the currently tested commit does not contain the bug.

### What does `git bisect bad` mean?

It tells Git that the currently tested commit contains the bug.

### How do you exit a bisect session?

```bash
git bisect reset
```
