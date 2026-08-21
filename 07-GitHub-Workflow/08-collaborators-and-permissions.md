# GitHub Collaborators & Permissions

GitHub collaborators are users who are given access to a repository so they can contribute to or manage the project.

Repository owners can control what collaborators are allowed to do by assigning them an appropriate repository role.

---

## Why Use Collaborators?

In a team environment, multiple developers may need access to the same repository.

Instead of giving everyone full administrative access, GitHub allows repository owners to assign different permission levels.

For example:

```text
Repository Owner
       ↓
Add Collaborators
       ↓
Assign Appropriate Role
       ↓
Collaborators Work on Repository
```

This follows the principle of giving users only the permissions they need.

---

# Adding a Collaborator

To add a collaborator:

```text
GitHub Repository
      ↓
Settings
      ↓
Collaborators
      ↓
Add people
```

GitHub provides a search field:

```text
Search by username, full name, or email
```

Search for the GitHub user you want to add, select the user, choose the appropriate role, and send the invitation.

The user must accept the invitation before the access becomes active.

---

# Repository Roles

GitHub provides different repository roles.

The main roles are:

```text
Read
Triage
Write
Maintain
Admin
```

Permissions increase from Read toward Admin.

---

## 1. Read

The **Read** role allows a user to view and access the repository.

A user with Read access can generally:

* View repository contents
* Clone the repository
* Download repository files
* View issues and Pull Requests

This role is suitable for users who only need to access or review the project.

---

## 2. Triage

The **Triage** role is mainly intended for managing issues and Pull Requests.

A Triage user can:

* Manage issues
* Manage Pull Requests
* Label issues
* Organize project discussions

They do not receive normal code-pushing permissions.

This is useful when someone needs to help manage project activity without modifying the repository code directly.

---

## 3. Write

The **Write** role allows a user to contribute code to the repository.

A user with Write access can generally:

* Push code
* Create branches
* Create Pull Requests
* Work with issues
* Contribute to the project

This is a common role for developers working on a team.

Example:

```text
Developer
    ↓
Write Access
    ↓
Create Branch
    ↓
Push Changes
    ↓
Pull Request
```

---

## 4. Maintain

The **Maintain** role provides broader repository management capabilities than Write.

A Maintainer can manage many aspects of the repository without having complete administrative control.

This role can be useful for project maintainers who need to manage the repository but should not have sensitive administrative permissions.

---

## 5. Admin

The **Admin** role provides full administrative control over the repository.

An administrator can manage things such as:

* Repository settings
* Access and permissions
* Collaborators
* Repository rules
* Security settings
* Other administrative features

Admin access should be given carefully because it provides extensive control over the repository.

---

# Permission Hierarchy

A simple way to remember the roles is:

```text
Read
  ↓
Triage
  ↓
Write
  ↓
Maintain
  ↓
Admin
```

As the role increases, the user receives more capabilities.

However, the roles are designed for different responsibilities rather than simply being levels of seniority.

---

# Practical Example

Consider a development team:

```text
Project Owner
      ↓
     Admin
      │
      ├── Developer → Write
      │
      ├── Project Manager → Triage
      │
      └── Reviewer → Read
```

Each person receives only the access required for their responsibilities.

---

# Managing Collaborators

Repository owners can manage existing collaborators from:

```text
Repository
    ↓
Settings
    ↓
Collaborators
```

From there, repository access can be reviewed and managed.

If a collaborator no longer needs access, the repository owner can remove their access.

---

# Collaborators vs Public Repository

A repository being **public** does not mean every user has permission to modify it.

For a public repository:

```text
Public Repository
      ↓
Anyone can view the repository
      ↓
Only users with appropriate write access
can directly contribute according to the repository rules
```

Public visibility and repository permissions are different concepts.

---

# Collaborators and Branch Protection

Collaborator permissions work together with branch protection rules.

For example:

```text
Developer
   ↓
Write permission
   ↓
Create feature branch
   ↓
Pull Request
   ↓
Branch protection rules
   ↓
Review / Approval
   ↓
main
```

Having Write access does not necessarily mean a developer can bypass the protection rules configured for `main`.

This allows teams to give developers the ability to contribute while still protecting important branches.

---

# Principle of Least Privilege

Users should receive only the permissions they need to perform their responsibilities.

For example:

```text
Need to view repository
        → Read

Need to manage issues/PRs
        → Triage

Need to push code
        → Write

Need to manage repository
        → Maintain

Need complete administration
        → Admin
```

This reduces the risk of accidental or unauthorized changes.

---

# Key Takeaway

**GitHub collaborators allow multiple users to work on a repository while repository roles control what each user is allowed to do.**

The five main repository roles are:

```text
Read → Triage → Write → Maintain → Admin
```

The correct role should be assigned based on the user's responsibilities rather than giving everyone full administrative access.
