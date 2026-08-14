# git fetch

## Overview

`git fetch` is used to download the latest commits, branches, and other information from a remote repository without automatically integrating those changes into the current local branch.

It is useful when you want to inspect remote changes before deciding whether to merge or rebase them.

## Syntax

```bash
git fetch <remote>
```

Example:

```bash
git fetch origin
```

To fetch from a specific branch:

```bash
git fetch origin feature1
```

## How It Works

Suppose new commits have been added to GitHub:

```text
Local Repository          Remote Repository

main                      origin/main
 A---B                    A---B---C---D
```

After:

```bash
git fetch origin
```

Git downloads the new commits:

```text
Local Repository

main
 A---B

origin/main
 A---B---C---D
```

Your local `main` branch has **not** been changed.

The remote-tracking branch `origin/main` now reflects the latest known state of the remote branch.

## Inspect Changes After Fetching

After running:

```bash
git fetch origin
```

you can compare your local branch with the remote branch:

```bash
git diff main origin/main
```

You can also view the commits that exist remotely but not locally:

```bash
git log main..origin/main --oneline
```

## Fetch All Remotes

To fetch updates from all configured remotes:

```bash
git fetch --all
```

## Fetch vs Pull

| Command | Purpose |
|---|---|
| `git fetch` | Downloads remote changes without integrating them |
| `git pull` | Downloads remote changes and integrates them |
| `git merge` | Integrates changes from another branch |
| `git rebase` | Replays commits onto another base |

Conceptually:

```text
git fetch
    ↓
Download remote changes
    ↓
Inspect changes
    ↓
Choose how to integrate
    ↓
git merge / git rebase
```

Whereas:

```text
git pull
    ↓
Fetch
    ↓
Integrate
```

## Practical Workflow

A cautious workflow is:

```bash
git fetch origin
```

Check the incoming commits:

```bash
git log main..origin/main --oneline
```

Compare the changes:

```bash
git diff main origin/main
```

Then integrate them if required:

```bash
git merge origin/main
```

## Important Points

- `git fetch` downloads information from a remote repository.
- It does not automatically modify the current local branch.
- It updates remote-tracking branches such as `origin/main`.
- It allows you to inspect remote changes before integrating them.
- `git pull` is different because it fetches and then integrates changes.
- `git fetch --all` fetches updates from all configured remotes.

## Interview Questions

### What is the purpose of `git fetch`?

`git fetch` downloads the latest information and commits from a remote repository without automatically integrating those changes into the current local branch.

### Why use `git fetch` instead of `git pull`?

`git fetch` allows you to inspect remote changes before integrating them, giving you more control over when and how those changes are incorporated into your local branch.

### What is `origin/main`?

`origin/main` is a remote-tracking branch that represents the latest state of the `main` branch known from the remote repository named `origin`.
