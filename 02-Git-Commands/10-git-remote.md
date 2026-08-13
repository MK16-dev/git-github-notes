# git remote

## Overview

`git remote` is used to manage connections between a local Git repository and remote repositories.

A remote repository is a version of the project hosted on a remote server such as GitHub.

The most commonly used remote name is `origin`.

## View Remote Repositories

To display the remote repositories configured for the current repository:

```bash
git remote
```

To display the remote names along with their URLs:

```bash
git remote -v
```

Example output:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

## Add a Remote Repository

To connect a local repository to a remote repository:

```bash
git remote add origin <repository-url>
```

Example:

```bash
git remote add origin https://github.com/username/project.git
```

Here:

- `remote` manages remote repositories.
- `add` adds a new remote connection.
- `origin` is the name assigned to the remote.
- `<repository-url>` is the URL of the remote repository.

## Verify the Remote

After adding the remote:

```bash
git remote -v
```

Example:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

## Change a Remote URL

To change the URL of an existing remote:

```bash
git remote set-url origin <new-repository-url>
```

Example:

```bash
git remote set-url origin https://github.com/username/new-project.git
```

## Remove a Remote

To remove a remote connection:

```bash
git remote remove origin
```

This removes the remote configuration from the local repository. It does not delete the remote repository itself.

## Fetch and Push URLs

A remote can have separate URLs for fetching and pushing.

```text
Fetch → Download information from the remote repository
Push  → Upload commits to the remote repository
```

The command:

```bash
git remote -v
```

shows both URLs.

## Typical Local-to-GitHub Workflow

A local repository can be connected to GitHub using:

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin <repository-url>
git push -u origin main
```

The remote connection allows the local repository to communicate with the GitHub repository.

## Important Points

- `git remote` manages remote repository connections.
- `origin` is the conventional name for the main remote repository.
- `git remote -v` displays remote URLs.
- `git remote add origin` connects a local repository to a remote repository.
- `git remote set-url` changes an existing remote URL.
- `git remote remove` removes a remote connection from the local repository.
- Removing a remote does not delete the repository hosted on GitHub.

## Interview Question

### What is the purpose of `git remote add origin`?

`git remote add origin` connects a local Git repository to a remote repository by assigning the remote repository the name `origin`.

### What is the difference between `git remote` and `git remote -v`?

`git remote` displays the names of configured remote repositories, while `git remote -v` displays the remote names along with their fetch and push URLs.
