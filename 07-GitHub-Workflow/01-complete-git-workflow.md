# Complete Git & GitHub Workflow

## Overview

A typical Git and GitHub workflow starts with creating or cloning a repository, making changes on a branch, committing those changes, pushing them to GitHub, and integrating them through a Pull Request.

The exact workflow can vary between teams, but the following process represents a common development workflow.

## Starting a New Local Project

Initialize Git inside the project:

```bash
git init
```

Check the repository:

```bash
git status
```

Configure the remote repository:

```bash
git remote add origin <repository-url>
```

## Create a Feature Branch

Create and switch to a feature branch:

```bash
git switch -c feature-login
```

Or:

```bash
git checkout -b feature-login
```

Working on a separate branch keeps feature development isolated from the main branch.

## Make Changes

Modify or create project files.

Check the changes:

```bash
git status
```

View the actual changes:

```bash
git diff
```

## Stage Changes

Stage the required files:

```bash
git add .
```

Or stage a specific file:

```bash
git add filename
```

## Commit Changes

Create a meaningful commit:

```bash
git commit -m "Add login feature"
```

The commit records the changes in the local repository.

## Push the Feature Branch

Push the branch to GitHub:

```bash
git push -u origin feature-login
```

The branch is now available on the remote repository.

## Create a Pull Request

On GitHub, create a Pull Request:

```text
feature-login → main
```

The changes can then be reviewed before being merged.

## Review and Update

If reviewers request changes:

```bash
git add .
git commit -m "Address review feedback"
git push
```

The existing Pull Request is automatically updated with the new commit.

## Merge the Feature

After approval, the feature branch can be merged into `main`.

The merge can happen through GitHub or locally.

Local merge example:

```bash
git switch main
git pull origin main
git merge feature-login
```

Then push the updated main branch:

```bash
git push origin main
```

## Delete the Feature Branch

After the feature has been successfully merged, the local branch can be deleted:

```bash
git branch -d feature-login
```

The remote branch can also be deleted:

```bash
git push origin --delete feature-login
```

## Keep the Local Main Branch Updated

Before starting another feature:

```bash
git switch main
git pull origin main
```

Then create a new feature branch:

```bash
git switch -c feature-profile
```

## Complete Workflow

```text
             GitHub Repository
                    ↑
                    |
                 git push
                    |
              Feature Branch
                    ↑
                    |
              git commit
                    ↑
                    |
               git add
                    ↑
                    |
              File Changes
                    |
                    ↓
              Pull Request
                    |
                    ↓
                Code Review
                    |
                    ↓
                  Merge
                    |
                    ↓
                  main
```

A more complete workflow:

```text
Clone / Initialize Repository
             ↓
        Create Branch
             ↓
        Make Changes
             ↓
        git add
             ↓
        git commit
             ↓
        git push
             ↓
      Create Pull Request
             ↓
        Code Review
             ↓
       Address Feedback
             ↓
           Merge
             ↓
        Update main
             ↓
       Delete Branch
```

## Keeping Work Updated

If other developers have pushed changes to the remote repository, update your local branch:

```bash
git pull origin main
```

For a more controlled workflow, fetch first:

```bash
git fetch origin
```

Then inspect or integrate the changes as required.

## Important Points

- Keep feature development on separate branches.
- Make small, meaningful commits.
- Use descriptive commit messages.
- Push feature branches to the remote repository.
- Use Pull Requests for review and collaboration.
- Keep the main branch stable.
- Update your local main branch before starting new work.
- Delete branches after they are no longer needed.
- Always verify the repository status before and after important operations.

## Example Command Sequence

A simplified feature workflow:

```bash
git switch main
git pull origin main

git switch -c feature-login

# Make changes

git status
git add .
git commit -m "Add login feature"

git push -u origin feature-login
```

Then:

```text
Create Pull Request
        ↓
Code Review
        ↓
Merge into main
        ↓
Delete feature branch
```

## Key Takeaway

Git provides the version-control system for managing changes, while GitHub provides collaboration features such as remote repositories, Pull Requests, code review, and repository hosting.

A good Git workflow keeps changes organized, reviewable, and easy to track throughout the development process.
