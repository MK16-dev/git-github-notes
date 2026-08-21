# Repository Rules & Branch Protection

Repository rules are used to control how changes can be made to important branches in a GitHub repository.

Branch protection helps prevent accidental or unauthorized changes to branches such as `main` and ensures that changes follow a controlled workflow.

---

## Why Use Branch Protection?

Without branch protection, a user with write access may be able to directly push changes to `main`:

```text
Developer
    ↓
git push
    ↓
main
```

This can cause problems such as:

* Accidental changes to production code
* Force-pushing and rewriting Git history
* Unreviewed code being merged
* Important branches being deleted

With branch protection, changes can follow a safer workflow:

```text
Feature Branch
      ↓
Pull Request
      ↓
Code Review
      ↓
Approval
      ↓
Merge
      ↓
main
```

---

# Creating a Repository Ruleset

Go to:

```text
GitHub Repository
      ↓
Settings
      ↓
Rules
      ↓
Rulesets
      ↓
New ruleset
      ↓
New branch ruleset
```

Give the ruleset a name.

Example:

```text
Protect main branch
```

Set the ruleset to:

```text
Active
```

Configure the target branch as:

```text
main
```

This means the rules will apply to the `main` branch.

---

# Rules Configured

For this practical setup, the following rules were enabled.

## 1. Restrict Deletions

This prevents users from deleting the protected `main` branch unless they have the required bypass permission.

This protects the important branch from accidental deletion.

---

## 2. Require a Pull Request Before Merging

This requires changes to be made on another branch and submitted through a Pull Request before they can be merged into `main`.

Instead of:

```text
Developer
    ↓
Direct Push
    ↓
main
```

the workflow becomes:

```text
Developer
    ↓
Feature Branch
    ↓
Pull Request
    ↓
Review
    ↓
Approval
    ↓
main
```

This is one of the most important branch protection rules.

---

## 3. Require Approvals

The ruleset was configured to require:

```text
Required approvals: 1
```

This means at least one approving review is required before the Pull Request can be merged.

This helps ensure that changes are reviewed by another person before reaching the protected branch.

---

## 4. Dismiss Stale Pull Request Approvals

This option was enabled.

When new reviewable commits are pushed to a Pull Request, previous approvals can be dismissed.

Example:

```text
Code submitted
     ↓
Reviewer approves
     ↓
New changes pushed
     ↓
Previous approval dismissed
     ↓
Review required again
```

This helps ensure that the latest changes are reviewed.

---

## 5. Require Conversation Resolution

This option was enabled.

All code review conversations must be resolved before the Pull Request can be merged.

For example:

```text
Reviewer:
"Please fix this issue."

        ↓

Developer fixes the issue

        ↓

Conversation resolved

        ↓

Pull Request can continue toward merging
```

---

## 6. Block Force Pushes

Force pushes were blocked for the protected branch.

Normally:

```bash
git push --force
```

can rewrite the history of a remote branch.

Blocking force pushes helps protect the history of `main` from being accidentally rewritten.

---

# Allowed Merge Methods

The ruleset was configured to allow:

```text
Squash
Rebase
```

### Squash Merge

Combines the commits from the Pull Request into a single commit when merging.

```text
Commit A
Commit B
Commit C
    ↓
Squash
    ↓
Single commit on main
```

### Rebase Merge

Replays the commits onto the target branch while maintaining a linear history.

These methods help keep the repository history clean.

---

# Practical Test

After creating the ruleset, a test branch was created:

```text
test-branch-protection
```

A change was pushed to the branch and a Pull Request was created:

```text
test-branch-protection
          ↓
      Pull Request
          ↓
         main
```

The Pull Request was successfully created.

GitHub then displayed:

```text
No reviews — at least 1 approving review is required.
```

This confirmed that the branch protection rule was working correctly.

The test Pull Request was then closed without merging, and the temporary test branch was deleted both locally and remotely.

---

# Recommended Workflow

With branch protection enabled, a typical workflow becomes:

```text
Create Feature Branch
        ↓
Make Changes
        ↓
Commit Changes
        ↓
Push Feature Branch
        ↓
Create Pull Request
        ↓
GitHub Actions / Status Checks
        ↓
Code Review
        ↓
Approval
        ↓
Resolve Conversations
        ↓
Merge Pull Request
        ↓
main
```

This is commonly used in professional development teams to protect important branches.

---

# Important Commands

Create a feature branch:

```bash
git checkout -b feature-name
```

Push the branch:

```bash
git push -u origin feature-name
```

After the Pull Request is merged, switch back to `main`:

```bash
git checkout main
```

Update `main`:

```bash
git pull origin main
```

Delete the local branch:

```bash
git branch -d feature-name
```

Delete a remote branch:

```bash
git push origin --delete feature-name
```

---

# Key Takeaway

**Branch protection ensures that important branches such as `main` cannot be changed carelessly.**

It can enforce rules such as:

```text
Pull Request required
        +
Approval required
        +
Conversations resolved
        +
Force pushes blocked
        +
Branch deletion restricted
```

This provides a safer and more controlled GitHub workflow for team-based development and CI/CD environments.

