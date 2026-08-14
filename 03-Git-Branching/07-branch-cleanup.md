# Branch Cleanup

## Overview

Feature branches are often created for individual features, fixes, or experiments.

After the changes have been merged into the main branch and the feature branch is no longer needed, it can be deleted to keep the repository organized.

## Delete a Local Branch

To delete a branch that has already been merged:

```bash
git branch -d feature2
```

The `-d` option performs a safe deletion. Git will normally prevent the deletion if the branch contains commits that have not been merged.

## Force Delete a Branch

To delete a branch even if it has not been merged:

```bash
git branch -D feature2
```

Use `-D` carefully because unmerged commits may become difficult to access after the branch is deleted.

## Verify the Branch Was Deleted

List local branches:

```bash
git branch
```

The deleted branch should no longer appear.

To check remote branches:

```bash
git branch -r
```

## Delete a Remote Branch

If a feature branch has also been pushed to GitHub, deleting the local branch does not automatically delete the remote branch.

To delete the remote branch:

```bash
git push origin --delete feature2
```

Afterward, the branch will be removed from the remote repository.

## Complete Feature Branch Workflow

A typical workflow looks like this:

### 1. Create a Feature Branch

```bash
git checkout -b feature2
```

### 2. Make Changes

Modify the project files as required.

### 3. Stage the Changes

```bash
git add .
```

### 4. Commit the Changes

```bash
git commit -m "Add feature2"
```

### 5. Push the Feature Branch

```bash
git push -u origin feature2
```

### 6. Switch to Main

```bash
git checkout main
```

### 7. Merge the Feature Branch

```bash
git merge feature2
```

### 8. Push the Updated Main Branch

```bash
git push origin main
```

### 9. Delete the Local Feature Branch

```bash
git branch -d feature2
```

### 10. Delete the Remote Feature Branch

If it is no longer needed on GitHub:

```bash
git push origin --delete feature2
```

## Workflow Summary

```text
             feature2
                |
          Make changes
                |
          git commit
                |
          git push -u origin feature2
                |
                ↓
              GitHub
                |
                ↓
          Pull Request
                |
                ↓
             main
                |
          git merge feature2
                |
          git push origin main
                |
                ↓
       Delete feature branch
```

## Important Points

- `git branch -d <branch>` safely deletes a merged local branch.
- `git branch -D <branch>` forcefully deletes a local branch.
- Deleting a local branch does not delete its remote counterpart.
- `git push origin --delete <branch>` deletes a remote branch.
- Feature branches are commonly deleted after their changes have been merged.
- Branch cleanup keeps repositories easier to maintain.

## Interview Question

### What is the difference between `git branch -d` and `git branch -D`?

`git branch -d` performs a safe deletion and normally prevents deletion of an unmerged branch, while `git branch -D` forcefully deletes the branch even if it contains unmerged changes.
