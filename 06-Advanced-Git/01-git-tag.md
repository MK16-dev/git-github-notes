# Git Tags

## Overview

Git tags are used to mark specific points in a repository's history.

They are commonly used to identify important versions or releases of a project.

For example:

```text
v1.0
v1.1
v2.0
```

Unlike branches, tags normally represent a fixed point in the Git history.

## View Tags

To list all tags:

```bash
git tag
```

Example:

```text
v1.0
v1.1
v2.0
```

## Create a Tag

To create a lightweight tag:

```bash
git tag v1.0
```

This creates a tag pointing to the current commit.

## Annotated Tags

Annotated tags contain additional information such as the tag message and tagger information.

Create an annotated tag:

```bash
git tag -a v1.0 -m "Release version 1.0"
```

Annotated tags are commonly preferred for official releases.

## Tag a Specific Commit

First find the commit:

```bash
git log --oneline
```

Example:

```text
a1b2c3d Add payment feature
e4f5g6h Add login feature
```

Create a tag for a specific commit:

```bash
git tag -a v1.0 a1b2c3d -m "Release version 1.0"
```

## View Tag Information

To see information about a tag:

```bash
git show v1.0
```

This displays the tag information and the commit associated with it.

## Push a Tag to GitHub

Creating a tag locally does not automatically push it to GitHub.

Push a specific tag:

```bash
git push origin v1.0
```

To push all local tags:

```bash
git push origin --tags
```

## Delete a Local Tag

To delete a local tag:

```bash
git tag -d v1.0
```

This removes the tag from your local repository.

## Delete a Remote Tag

To remove a tag from the remote repository:

```bash
git push origin --delete v1.0
```

## Tags vs Branches

| Feature | Tag | Branch |
|---|---|---|
| Purpose | Mark a specific point | Continue development |
| Usually moves | No | Yes |
| Common use | Releases/versions | Features/fixes |
| Example | `v1.0` | `feature-login` |

Example:

```text
A---B---C---D---E
        ↑       ↑
       v1.0    v2.0
```

The tags identify specific commits.

A branch, on the other hand, continues moving as new commits are added.

## Typical Release Workflow

A simple release workflow can be:

```bash
git checkout main
git pull origin main
git tag -a v1.0 -m "Release version 1.0"
git push origin v1.0
```

The GitHub repository can then use the tag to identify that release version.

## Important Points

- Tags mark specific points in Git history.
- Tags are commonly used for project releases.
- Lightweight tags contain a simple reference to a commit.
- Annotated tags contain additional metadata.
- Tags do not automatically move when new commits are created.
- Tags must be pushed separately if you want them on the remote repository.
- `git push origin --tags` pushes all local tags.

## Interview Questions

### What is a Git tag?

A Git tag is a reference used to mark a specific commit in the repository's history.

### Why are tags used?

Tags are commonly used to identify important versions or releases of a project.

### What is the difference between a tag and a branch?

A tag normally points to a fixed commit, while a branch is a movable reference that advances as new commits are added.

### How do you create an annotated tag?

```bash
git tag -a v1.0 -m "Release version 1.0"
```

### How do you push a tag to GitHub?

```bash
git push origin v1.0
```
