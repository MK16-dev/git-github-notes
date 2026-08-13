# git rm and git mv

## git rm

### Overview

`git rm` is used to remove files from both the working directory and the Git repository's index.

It is useful when a file should no longer be part of the project.

### Syntax

```bash
git rm <file-name>
```

### Example

```bash
git rm old-file.txt
```

This removes `old-file.txt` from the working directory and stages its deletion for the next commit.

Afterward, create a commit:

```bash
git commit -m "Remove old file"
```

### Remove Multiple Files

```bash
git rm file1.txt file2.txt
```

### Remove a File from Git but Keep It Locally

To stop tracking a file while keeping it in the working directory:

```bash
git rm --cached <file-name>
```

Example:

```bash
git rm --cached config.txt
```

This is commonly useful when a file should no longer be tracked, such as when adding it to `.gitignore`.

---

## git mv

### Overview

`git mv` is used to move or rename a file while allowing Git to track the change.

### Syntax

```bash
git mv <old-name> <new-name>
```

### Rename a File

```bash
git mv old-name.txt new-name.txt
```

Git stages the rename automatically.

### Move a File

```bash
git mv README.md docs/README.md
```

This moves `README.md` into the `docs` directory and stages the change.

### Check the Status

After using `git mv`:

```bash
git status
```

Git will show the rename or move as a staged change.

---

## `git rm` vs `git mv`

| Command | Purpose |
|---|---|
| `git rm <file>` | Remove a file and stage its deletion |
| `git rm --cached <file>` | Stop tracking a file while keeping it locally |
| `git mv <old> <new>` | Rename or move a file and stage the change |

## Important Points

- `git rm` removes a file from the working directory and stages the deletion.
- `git rm --cached` removes a file from Git tracking but keeps it locally.
- `git mv` can be used to rename or move files.
- Changes made using `git rm` and `git mv` should be committed to permanently record them in the repository.

## Interview Question

### What is the difference between `git rm` and `git rm --cached`?

`git rm` removes a file from both the working directory and Git's tracking, while `git rm --cached` removes the file from Git's tracking but keeps the file in the working directory.
