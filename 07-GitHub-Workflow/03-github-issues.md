# GitHub Issues

## Overview

GitHub Issues is a feature used to track tasks, bugs, feature requests, improvements, and other work related to a repository.

Instead of keeping tasks in separate documents or messages, teams can track them directly inside the GitHub repository.

## Common Uses

GitHub Issues can be used for:

- Reporting bugs
- Requesting new features
- Tracking development tasks
- Planning improvements
- Discussing problems
- Organizing project work

## Creating an Issue

To create an issue on GitHub:

1. Open the repository.
2. Go to the **Issues** section.
3. Select **New issue**.
4. Add a descriptive title.
5. Explain the problem or task.
6. Add labels if required.
7. Assign the issue to a team member if needed.
8. Create the issue.

Example:

```text
Title:
Fix login validation error

Description:
Users are able to submit the login form
without entering an email address.
```

## Issue Labels

Labels help categorize issues.

Common examples:

```text
bug
feature
enhancement
documentation
question
good first issue
```

For example:

```text
Fix login validation error
        ↓
      bug
```

Labels make it easier to filter and organize project work.

## Assigning Issues

An issue can be assigned to one or more contributors.

For example:

```text
Issue: Fix login validation
Assigned to: Developer
```

This makes it clear who is responsible for working on the task.

## Linking Issues to Pull Requests

A Pull Request can be connected to an issue.

For example, a Pull Request description can contain:

```text
Fixes #12
```

When the Pull Request is merged into the default branch, GitHub can automatically close the referenced issue.

Other keywords can also be used, such as:

```text
Closes #12
Resolves #12
Fixes #12
```

## Issue Workflow

A typical workflow can look like:

```text
Identify a Problem
       ↓
Create GitHub Issue
       ↓
Assign / Label Issue
       ↓
Create Feature Branch
       ↓
Implement Changes
       ↓
Create Pull Request
       ↓
Link PR to Issue
       ↓
Code Review
       ↓
Merge PR
       ↓
Issue Closed
```

## Issues vs Pull Requests

These two features serve different purposes.

### GitHub Issue

Used to describe and track a task, bug, question, or feature request.

### Pull Request

Used to propose and review actual code changes.

Simple way to remember:

```text
Issue
  ↓
What needs to be done?

Pull Request
  ↓
Here is the code that does it.
```

## Example

Suppose a user reports:

```text
Issue #25
Login button does not work
```

A developer can create:

```text
feature/fix-login
```

After implementing the fix:

```bash
git add .
git commit -m "Fix login button"
git push -u origin feature/fix-login
```

Then create a Pull Request with:

```text
Fixes #25
```

After the Pull Request is reviewed and merged, GitHub can automatically close Issue #25.

## Important Points

- GitHub Issues help track project work.
- Issues can represent bugs, features, tasks, and questions.
- Labels help categorize issues.
- Issues can be assigned to contributors.
- Pull Requests can be linked to Issues.
- Keywords such as `Fixes`, `Closes`, and `Resolves` can automatically close linked issues when the Pull Request is merged.
- Issues and Pull Requests are complementary but serve different purposes.

## Interview Questions

### What is a GitHub Issue?

A GitHub Issue is a tool for tracking bugs, tasks, feature requests, questions, and other work within a repository.

### What is the difference between an Issue and a Pull Request?

An Issue describes or tracks work that needs to be done, while a Pull Request proposes code changes that implement or address that work.

### Can an Issue be linked to a Pull Request?

Yes. For example:

```text
Fixes #12
```

can link a Pull Request to Issue #12.

### What happens when a linked Pull Request is merged?

If a supported closing keyword such as `Fixes #12` is used, GitHub can automatically close the linked issue when the Pull Request is merged into the default branch.

### Why are labels useful?

Labels help categorize, filter, and organize issues so teams can quickly understand what type of work is required.
