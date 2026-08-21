# GitHub Actions Secrets

GitHub Actions Secrets are used to securely store sensitive information such as passwords, API keys, tokens, and credentials that are required by a GitHub Actions workflow.

Instead of writing sensitive values directly inside the workflow file, we store them as **GitHub Secrets** and access them through the `${{ secrets.SECRET_NAME }}` syntax.

---

## Why Use GitHub Actions Secrets?

Sensitive information should not be hardcoded in workflow files because workflow files are stored in the Git repository.

For example, we should **not** do this:

```yaml
env:
  PASSWORD: mypassword123
```

Instead, we store the password as a GitHub Secret and use:

```yaml
env:
  PASSWORD: ${{ secrets.PASSWORD }}
```

This helps prevent sensitive credentials from being exposed in the repository.

---

## Creating a GitHub Actions Secret

1. Open the required repository on GitHub.

2. Go to:

```text
Settings → Secrets and variables → Actions
```

3. Under **Repository secrets**, click:

```text
New repository secret
```

4. Enter the secret name.

Example:

```text
MY_SECRET
```

5. Enter the sensitive value in the **Secret** field.

6. Click:

```text
Add secret
```

The secret is now securely stored in the GitHub repository and can be accessed by GitHub Actions workflows.

---

## Using a Secret in a GitHub Actions Workflow

Secrets can be accessed using:

```yaml
${{ secrets.SECRET_NAME }}
```

Example:

```yaml
name: Secret Demo

on:
  push:
    branches:
      - main

jobs:
  secret-demo:
    runs-on: ubuntu-latest

    steps:
      - name: Use Secret
        run: echo "Secret is configured"
        env:
          MY_SECRET: ${{ secrets.MY_SECRET }}
```

Here:

* `secrets` refers to GitHub Actions Secrets.
* `MY_SECRET` is the name of the secret created in the repository.
* `${{ secrets.MY_SECRET }}` retrieves the secret value.
* The secret is passed to the step through an environment variable.

---

## Important Points

* Never hardcode passwords, API keys, tokens, or other sensitive credentials in workflow files.
* Store sensitive values in **GitHub Secrets**.
* Use `${{ secrets.SECRET_NAME }}` to access a secret inside a workflow.
* Secret names are case-sensitive, so use the exact name configured in GitHub.
* Secrets are intended to prevent sensitive values from being stored directly in the repository.
* Do not intentionally print secret values in workflow logs.
* If a secret is accidentally exposed, it should be revoked or rotated immediately.

---

## Repository Secrets vs Environment Secrets

GitHub Actions supports different levels of secrets.

### Repository Secrets

Repository secrets are available to workflows in the repository when permitted.

They can be accessed using:

```yaml
${{ secrets.SECRET_NAME }}
```

### Environment Secrets

Secrets can also be associated with a specific GitHub Environment, such as:

```text
development
staging
production
```

This is useful when different environments require different credentials.

For example:

```text
Development → DEV_API_KEY
Production  → PROD_API_KEY
```

This allows the workflow to use environment-specific secrets without placing the actual values inside the workflow file.

---

## Practical Example

Suppose a project needs an API key.

Instead of putting the API key directly in:

```yaml
API_KEY: abc123
```

we create a GitHub Secret:

```text
API_KEY
```

Then use:

```yaml
env:
  API_KEY: ${{ secrets.API_KEY }}
```

The workflow can now use the API key without storing its actual value in the Git repository.

---

## Key Takeaway

**GitHub Actions Secrets provide a secure way to manage sensitive information required by CI/CD workflows without hardcoding credentials directly into the workflow files.**

The basic process is:

```text
Create Secret in GitHub
        ↓
Store sensitive value
        ↓
Reference it in workflow
        ↓
${{ secrets.SECRET_NAME }}
        ↓
Use it in the GitHub Actions job
```
