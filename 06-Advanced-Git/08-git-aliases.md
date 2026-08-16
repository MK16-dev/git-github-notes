# Git Aliases

## Overview

Git aliases allow you to create shorter names for frequently used Git commands.

They can make commonly used commands faster to type and easier to remember.

For example, instead of repeatedly typing:

```bash
git status
```

you can create an alias such as:

```bash
git st
```

## Create an Alias

To create an alias for `git status`:

```bash
git config --global alias.st status
```

Now you can use:

```bash
git st
```

instead of:

```bash
git status
```

## Common Aliases

### Status

```bash
git config --global alias.st status
```

Usage:

```bash
git st
```

### Log

A compact log alias:

```bash
git config --global alias.lg "log --oneline --graph --decorate --all"
```

Usage:

```bash
git lg
```

### Last Commit

```bash
git config --global alias.last "log -1 HEAD"
```

Usage:

```bash
git last
```

## View Configured Aliases

Git aliases are stored in Git configuration.

To view your Git configuration:

```bash
git config --global --list
```

You can also check a specific alias:

```bash
git config --global alias.st
```

## Remove an Alias

To remove an alias:

```bash
git config --global --unset alias.st
```

The alias will no longer be available.

## Why Use Aliases?

Aliases are useful when:

- A command is used frequently.
- A command is long and repetitive.
- You want a consistent personal Git workflow.
- You want frequently used log or status commands to be easier to type.

## Example Workflow

Without an alias:

```bash
git status
git log --oneline --graph --decorate --all
```

With aliases:

```bash
git st
git lg
```

The underlying Git commands remain the same; the alias simply provides a shorter way to invoke them.

## Important Points

- Git aliases create shortcuts for Git commands.
- Aliases can be configured globally or for a specific repository.
- `--global` applies the alias to repositories for the current user.
- `git config --global --list` can be used to view global configuration.
- Aliases do not create new Git commands; they provide alternate names for existing commands.

## Interview Questions

### What is a Git alias?

A Git alias is a custom shortcut for an existing Git command.

### How do you create an alias for `git status`?

```bash
git config --global alias.st status
```

Then:

```bash
git st
```

can be used instead of:

```bash
git status
```

### How do you remove a Git alias?

```bash
git config --global --unset alias.st
```

### What does `--global` mean?

It applies the configuration to the current user's Git configuration, making the alias available across their repositories.
