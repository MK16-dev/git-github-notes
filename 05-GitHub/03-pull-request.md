# Pull Request

## Overview

A Pull Request (PR) is a feature provided by platforms such as GitHub that allows developers to propose changes from one branch to another.

A Pull Request is commonly used to review and merge changes from a feature branch into the main branch.

A Pull Request is **not a Git command**. It is a collaboration and code-review feature provided by Git hosting platforms.

## Typical Workflow

A common feature development workflow is:

```text
main
  |
  | Create feature branch
  ↓
feature1
  |
  | Make changes
  | git add .
  | git commit
  ↓
feature1
  |
  | git push
  ↓
GitHub
  |
  | Create Pull Request
  ↓
Code Review
  |
  | Approve / Request Changes
  ↓
Merge
  ↓
main
```

## Create a Feature Branch

Create and switch to a new branch:

```bash
git switch -c feature1
```

Or using `checkout`:

```bash
git checkout -b feature1
```

## Make and Commit Changes

After making changes:

```bash
git add .
```

Create a commit:

```bash
git commit -m "Add feature1"
```

## Push the Branch

Push the branch to GitHub:

```bash
git push -u origin feature1
```

After the branch is pushed, GitHub may provide an option to create a Pull Request.

## Create a Pull Request

On GitHub, select:

```text
feature1 → main
```

The Pull Request can include:

- A title
- A description
- Reviewers
- Code changes
- Comments

The team can review the proposed changes before merging them.

## Review Process

A typical Pull Request review may involve:

```text
Pull Request
     ↓
Code Review
     ↓
Approved?
   /     \
 Yes      No
  |        |
  ↓        ↓
Merge    Make changes
           |
           ↓
        Push again
```

If changes are requested, make the changes locally:

```bash
git add .
git commit -m "Address review comments"
git push
```

The Pull Request is automatically updated with the new commit.

## Merge a Pull Request

Once the changes have been reviewed and approved, the Pull Request can be merged into the target branch.

For example:

```text
feature1 → main
```

After merging, the feature branch can usually be deleted if it is no longer needed.

## Pull Request vs `git merge`

These are related but different.

### Pull Request

A GitHub feature used to propose, review, discuss, and merge changes.

### `git merge`

A Git command used to combine changes from one branch into another.

Example:

```bash
git checkout main
git merge feature1
```

A Pull Request can ultimately result in a merge, but the review process happens through GitHub.

## Pull Request vs Push

`git push` uploads local commits to a remote repository:

```bash
git push origin feature1
```

A Pull Request proposes that those changes be integrated into another branch.

```text
git push
    ↓
Branch appears on GitHub
    ↓
Pull Request
    ↓
Review
    ↓
Merge
```

## Important Points

- A Pull Request is primarily a GitHub collaboration feature.
- It allows developers to propose changes for review.
- Pull Requests are commonly created from feature branches.
- A Pull Request can be updated by pushing additional commits to the same branch.
- Pull Requests help with code review and collaboration.
- A Pull Request is not the same as `git merge`.
- `git push` uploads commits; a Pull Request proposes integrating those commits into another branch.

## Interview Questions

### What is a Pull Request?

A Pull Request is a GitHub feature used to propose changes from one branch to another and allow those changes to be reviewed before they are merged.

### Is a Pull Request a Git command?

No. A Pull Request is a feature provided by Git hosting platforms such as GitHub.

### What happens after creating a Pull Request?

The changes can be reviewed, discussed, modified if necessary, approved, and eventually merged into the target branch.

### Can you update an existing Pull Request?

Yes. Push additional commits to the same branch, and GitHub will automatically update the Pull Request.
