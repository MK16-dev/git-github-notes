# First GitHub Actions Workflow

## Objective

Create a simple GitHub Actions workflow that automatically runs whenever code is pushed to the `main` branch.

The workflow will:

1. Start a GitHub Actions runner.
2. Check out the repository.
3. Run a simple command.
4. Display the result in the Actions tab.

## Workflow File

GitHub Actions workflow files are stored inside:

```text
.github/workflows/
```

Create a file such as:

```text
.github/
└── workflows/
    └── ci.yml
```

## Basic Workflow

```yaml
name: CI

on:
  push:
    branches:
      - main

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Run test command
        run: echo "GitHub Actions is working!"
```

## Understanding the Workflow

### name

```yaml
name: CI
```

Defines the name of the workflow.

GitHub displays this name in the Actions section.

### on

```yaml
on:
  push:
    branches:
      - main
```

Defines when the workflow should run.

In this example, it runs whenever code is pushed to the `main` branch.

### jobs

```yaml
jobs:
```

Defines the jobs that the workflow will execute.

### Job Name

```yaml
test:
```

`test` is the identifier for the job.

### runs-on

```yaml
runs-on: ubuntu-latest
```

Specifies the operating system used by the GitHub Actions runner.

### steps

```yaml
steps:
```

Contains the individual tasks performed by the job.

### uses

```yaml
uses: actions/checkout@v4
```

Uses a pre-built GitHub Action to check out the repository code.

### run

```yaml
run: echo "GitHub Actions is working!"
```

Runs a shell command on the runner.

## Complete Workflow

```text
Developer pushes code
        ↓
GitHub detects push
        ↓
GitHub Actions workflow starts
        ↓
Runner starts
        ↓
Repository checked out
        ↓
Command executed
        ↓
Workflow result displayed
```

## Viewing the Workflow

After pushing the workflow file to GitHub:

1. Open the repository on GitHub.
2. Select the **Actions** tab.
3. Find the `CI` workflow.
4. Open the workflow run.
5. Select the `test` job.
6. Expand the steps to view their output.

A successful workflow will show a successful status.

## Updating the Workflow

You can add more commands:

```yaml
- name: Show Git version
  run: git --version

- name: Show current directory
  run: pwd

- name: List files
  run: ls
```

This allows you to see what the GitHub Actions runner is doing.

## Important Points

- Workflow files use YAML.
- Workflow files are stored in `.github/workflows/`.
- `on` defines the event that triggers a workflow.
- `jobs` defines the work to be performed.
- `runs-on` specifies the runner environment.
- `steps` contain individual tasks.
- `uses` runs a reusable action.
- `run` executes a shell command.
- Workflow results can be viewed from the GitHub Actions tab.

## Key Takeaway

A GitHub Actions workflow automatically performs tasks when a configured event occurs.

This is the foundation of CI/CD:

```text
Code Change
    ↓
GitHub
    ↓
GitHub Actions
    ↓
Build / Test
    ↓
Result
```
