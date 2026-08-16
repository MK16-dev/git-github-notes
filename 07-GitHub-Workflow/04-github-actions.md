# GitHub Actions

## Overview

GitHub Actions is a CI/CD and automation platform built into GitHub.

It allows you to automatically run tasks when events occur in a repository.

Common tasks include:

- Running tests
- Building applications
- Checking code quality
- Deploying applications
- Running scripts
- Automating development workflows

## What is CI/CD?

### Continuous Integration (CI)

Continuous Integration means automatically building and testing code whenever changes are added to a repository.

Example:

```text
Developer pushes code
        ↓
GitHub Actions starts
        ↓
Install dependencies
        ↓
Run tests
        ↓
Build application
```

### Continuous Delivery / Deployment (CD)

CD automates the process of delivering or deploying an application after the code passes the required checks.

Example:

```text
Code
 ↓
Build
 ↓
Test
 ↓
Deploy
```

## Workflow

A GitHub Actions workflow is an automated process defined in a YAML file.

Workflow files are stored inside:

```text
.github/workflows/
```

Example:

```text
repository/
└── .github/
    └── workflows/
        └── ci.yml
```

## Basic Workflow Structure

A workflow can contain:

```yaml
name: CI

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Run a command
        run: echo "Hello GitHub Actions"
```

## Main Components

### Workflow

The complete automated process.

Example:

```text
CI Workflow
```

### Event

Defines when the workflow should run.

Examples:

```yaml
on:
  push:
```

or:

```yaml
on:
  pull_request:
```

### Job

A group of steps that are executed together.

Example:

```yaml
jobs:
  build:
```

### Runner

The machine used to execute the job.

Example:

```yaml
runs-on: ubuntu-latest
```

### Step

An individual task inside a job.

Example:

```yaml
steps:
  - name: Run tests
    run: npm test
```

## Common GitHub Actions Events

### Push

Runs when code is pushed:

```yaml
on:
  push:
```

### Pull Request

Runs when a Pull Request is opened or updated:

```yaml
on:
  pull_request:
```

### Manual Trigger

A workflow can also be started manually:

```yaml
on:
  workflow_dispatch:
```

## Actions

GitHub Actions provides reusable actions that can perform common tasks.

For example:

```yaml
- uses: actions/checkout@v4
```

This checks out the repository code so that later steps can work with it.

## Run Commands

Commands can be executed using `run`:

```yaml
- name: Display Git version
  run: git --version
```

Multiple commands can also be written:

```yaml
- name: Install dependencies
  run: |
    npm install
    npm test
```

## GitHub Actions Workflow

A typical CI workflow looks like:

```text
Developer pushes code
        ↓
GitHub detects event
        ↓
Workflow starts
        ↓
Runner is created
        ↓
Repository is checked out
        ↓
Dependencies installed
        ↓
Tests executed
        ↓
Build performed
        ↓
Result reported
```

## CI/CD Example

For a Node.js project:

```text
Push code
   ↓
Checkout code
   ↓
Install Node.js
   ↓
npm install
   ↓
npm test
   ↓
npm run build
```

For a Java project:

```text
Push code
   ↓
Checkout code
   ↓
Set up JDK
   ↓
Build with Maven
   ↓
Run tests
   ↓
Generate build artifact
```

## GitHub Actions and DevOps

GitHub Actions is commonly used in DevOps pipelines.

A simple DevOps workflow can be:

```text
Git
 ↓
GitHub
 ↓
GitHub Actions
 ↓
Build
 ↓
Test
 ↓
Docker
 ↓
Cloud Deployment
```

This allows repetitive development and deployment tasks to be automated.

## Important Points

- GitHub Actions is used for automation and CI/CD.
- Workflows are written in YAML.
- Workflow files are stored in `.github/workflows/`.
- Events determine when workflows run.
- Jobs contain groups of steps.
- Runners execute jobs.
- Actions are reusable components.
- `run` executes shell commands.
- GitHub Actions can automate testing, building, and deployment.

## Interview Questions

### What is GitHub Actions?

GitHub Actions is a GitHub automation platform used to create CI/CD workflows and automate development tasks.

### Where are GitHub Actions workflow files stored?

They are stored in:

```text
.github/workflows/
```

### What is a workflow?

A workflow is an automated process defined using a YAML file.

### What is a runner?

A runner is the machine that executes the jobs and steps defined in a GitHub Actions workflow.

### What is the difference between a job and a step?

A job is a group of steps that runs on a runner. A step is an individual task inside that job.

### Why is GitHub Actions useful in DevOps?

It can automate processes such as testing, building, packaging, and deploying applications, reducing manual work and creating a repeatable CI/CD pipeline.
