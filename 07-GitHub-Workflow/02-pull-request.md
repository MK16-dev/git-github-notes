# Pull Requests

## Overview

A Pull Request (PR) is a way to propose changes from one branch to another on GitHub.

Pull Requests are commonly used for:

- Code review
- Collaboration
- Discussing changes
- Running automated checks
- Safely merging feature work into the main branch

A common workflow is:

```text
feature branch
      ↓
   git push
      ↓
GitHub Pull Request
      ↓
Code Review
      ↓
Approval
      ↓
Merge
      ↓
main
```

## Create a Feature Branch

Start by creating a separate branch:

```bash
git switch -c feature-login
```

Or:

```bash
git checkout -b feature-login
```

## Make and Commit Changes

After making changes:

```bash
git status
```

Stage the changes:

```bash
git add .
```

Commit them:

```bash
git commit -m "Add login feature"
```

## Push the Branch

Push the feature branch to GitHub:

```bash
git push -u origin feature-login
```

The branch will now be available on the remote repository.

## Create a Pull Request

On GitHub:

1. Open the repository.
2. Select the pushed feature branch.
3. Choose **Compare & pull request**.
4. Select the target branch, usually `main`.
5. Add a meaningful title.
6. Explain what was changed.
7. Create the Pull Request.

The PR will look conceptually like:

```text
feature-login  ─────────→  main
                    Pull Request
```

## Pull Request Review

Other developers can review the proposed changes.

They may:

- Approve the changes.
- Request changes.
- Leave comments.
- Discuss implementation details.

If changes are requested, make additional commits on the same branch:

```bash
git add .
git commit -m "Address review feedback"
git push
```

The Pull Request automatically reflects the new commits.

## Merge the Pull Request

Once the changes are approved and checks pass, the Pull Request can be merged into the target branch.

Common merge options on GitHub include:

```text
Create a merge commit
Squash and merge
Rebase and merge
```

The exact options available depend on the repository settings.

## Delete the Feature Branch

After merging, the feature branch can be deleted.

GitHub usually provides a button to delete the remote branch.

You can also delete it locally:

```bash
git branch -d feature-login
```

To delete the remote branch manually:

```bash
git push origin --delete feature-login
```

## Complete Pull Request Workflow

```text
Create feature branch
        ↓
Make changes
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
Changes requested?
     ↙       ↘
   Yes        No
    ↓          ↓
Make changes  Approval
    ↓          ↓
git push      Merge
    ↓          ↓
PR updated    main
```

## Pull Request vs git merge

These are related but not the same thing.

### Pull Request

A GitHub collaboration feature used to propose and review changes before merging.

### git merge

A Git command that combines changes from one branch into another.

Example:

```bash
git merge feature-login
```

A Pull Request may eventually result in a merge, but the review process happens through GitHub.

## Important Points

- Pull Requests are created on platforms such as GitHub.
- A PR proposes changes from one branch to another.
- PRs support code review and discussion.
- Additional commits can be pushed to an open PR.
- A PR can be merged after review and required checks.
- Feature branches are commonly used for Pull Requests.
- A PR is not the same thing as the `git merge` command.

## Interview Questions

### What is a Pull Request?

A Pull Request is a request to merge changes from one branch into another, usually with a code-review process before merging.

### Why are Pull Requests used?

They allow teams to review, discuss, test, and approve code changes before integrating them into the main codebase.

### Can you update an existing Pull Request?

Yes. Push additional commits to the same source branch and the Pull Request will automatically update.

### What happens after a Pull Request is merged?

The changes are integrated into the target branch, such as `main`. The feature branch can then usually be deleted.

### Is a Pull Request a Git command?

No. A Pull Request is a collaboration feature provided by Git hosting platforms such as GitHub.
