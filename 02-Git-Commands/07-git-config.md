# git config

## Overview

`git config` is used to view and modify Git configuration settings.

Git configuration controls settings such as the user's name, email address, default behavior, and other repository-related options.

## Configure User Name

Set the name that will be associated with your commits:

```bash
git config --global user.name "Your Name"
```

Example:

```bash
git config --global user.name "Mital Kale"
```

## Configure User Email

Set the email address that will be associated with your commits:

```bash
git config --global user.email "your-email@example.com"
```

Example:

```bash
git config --global user.email "mital@example.com"
```

The email should generally match the email associated with your GitHub account if you want your commits to be correctly associated with your GitHub profile.

## View Git Configuration

To display all currently configured Git settings:

```bash
git config --list
```

To view a specific setting:

```bash
git config user.name
```

```bash
git config user.email
```

## Configuration Levels

Git provides three main configuration levels:

### System

Applies to all users on the computer:

```bash
git config --system
```

### Global

Applies to the current user across all repositories:

```bash
git config --global
```

### Local

Applies only to the current repository:

```bash
git config --local
```

The local configuration takes precedence over the global configuration.

## Example

Set the global identity:

```bash
git config --global user.name "Mital Kale"
git config --global user.email "your-email@example.com"
```

Check the configuration:

```bash
git config --list
```

## Important Commands

| Command | Purpose |
|---|---|
| `git config --global user.name "Name"` | Set global username |
| `git config --global user.email "Email"` | Set global email |
| `git config --list` | Display Git configuration |
| `git config user.name` | Display configured username |
| `git config user.email` | Display configured email |

## Important Points

- Git uses `user.name` and `user.email` to identify the author of commits.
- `--global` applies the configuration to all repositories for the current user.
- `--local` applies the configuration only to the current repository.
- `--system` applies the configuration to the entire system.
- Local configuration takes precedence over global configuration.

## Interview Question

### Why is `git config user.name` and `git config user.email` required?

Git uses these values to associate commits with an author. They are stored as part of the commit information and help identify who made the changes.
