# git remote

## Overview

A remote is a reference to a repository hosted somewhere outside your local repository.

A remote repository is commonly hosted on platforms such as GitHub.

Git uses remote names to identify these repositories. The most common default remote name is:

```text
origin
```

## View Remote Repositories

To view the remote repositories configured for the current repository:

```bash
git remote
```

Example:

```text
origin
```

## View Remote URLs

To see the URLs associated with the configured remotes:

```bash
git remote -v
```

Example:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

The output shows separate URLs for fetching and pushing.

## Add a Remote Repository

To connect an existing local repository to a remote repository:

```bash
git remote add origin <repository-url>
```

Example:

```bash
git remote add origin https://github.com/username/project.git
```

Here:

- `git remote add` adds a remote repository.
- `origin` is the name assigned to the remote.
- `<repository-url>` is the URL of the remote repository.

## Verify the Remote

After adding the remote:

```bash
git remote -v
```

You should see the configured remote URL.

## Push to the Remote

Once the remote has been configured, you can push your local branch:

```bash
git push -u origin main
```

The first part:

```text
origin
```

identifies the remote repository.

The second part:

```text
main
```

identifies the branch being pushed.

## Change a Remote URL

If the remote URL needs to be changed:

```bash
git remote set-url origin <new-url>
```

Example:

```bash
git remote set-url origin https://github.com/username/new-project.git
```

Verify the change:

```bash
git remote -v
```

## Rename a Remote

To rename a remote:

```bash
git remote rename origin upstream
```

This changes the remote name from `origin` to `upstream`.

The default name `origin` is normally sufficient for a typical personal repository.

## Remove a Remote

To remove a configured remote:

```bash
git remote remove origin
```

This removes the remote reference from your local repository.

It does not delete the actual GitHub repository.

## Local Repository and Remote Repository

The relationship can be represented as:

```text
Local Repository
       |
       | git remote add origin
       ↓
Remote Repository
       |
       | git push
       ↓
     GitHub
```

Changes can also move in the opposite direction:

```text
GitHub
   |
   | git fetch / git pull
   ↓
Local Repository
```

## Important Points

- A remote represents a repository hosted elsewhere.
- `origin` is the conventional default name for the primary remote.
- `git remote` lists configured remote names.
- `git remote -v` displays remote URLs.
- `git remote add origin <URL>` connects a local repository to a remote.
- `git remote set-url` changes a remote URL.
- `git remote remove` removes a remote reference from the local repository.
- Removing a remote does not delete the remote repository itself.

## Interview Questions

### What is a Git remote?

A Git remote is a reference to a repository hosted outside the local repository, commonly on a platform such as GitHub.

### What is `origin`?

`origin` is the conventional name given to the primary remote repository when a repository is cloned or when a remote is added manually.

### What does `git remote -v` do?

It displays the URLs configured for the repository's remotes for fetching and pushing.

### What does this command do?

```bash
git remote add origin <URL>
```

It adds a remote repository and gives it the name `origin`.
