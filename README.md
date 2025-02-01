The `checkout-if-exists` GitHub Action is designed to streamline your CI/CD workflows by conditionally checking out a specific branch from a repository. If the specified branch exists, it will be checked out; otherwise, the action defaults to the repository's default branch.

**Features:**

- **Conditional Branch Checkout:** Checks out a specified branch if it exists.
- **Fallback to Default Branch:** If the specified branch doesn't exist, it automatically checks out the repository's default branch.

**Usage:**

To utilize the `checkout-if-exists` action in your workflow, include it as a step in your GitHub Actions workflow file (`.github/workflows/your-workflow.yml`).

```yaml
name: Conditional Branch Checkout Workflow

on:
  push:
    branches:
      - main

jobs:
  checkout:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout with Fallback
        uses: PlentifulApp/checkout-if-exists@v1
        with:
          ref-if-exists: 'feature-branch'  # Replace with your target branch name
          ref-fallback: 'main'            # Replace with your fallback branch name (optional)
```

**Inputs:**

- `ref-if-exists`: The name of the branch to check out if it exists.
- `ref-fallback`: The name of the branch to check out if `ref-if-exists` does not exist. Defaults to the repository's default branch if not specified.

**Example:**

If you want to check out the `feature-branch` if it exists, and fall back to the default branch if it doesn't, your configuration would be:

```yaml
- name: Checkout with Fallback
  uses: PlentifulApp/checkout-if-exists@v1
  with:
    ref-if-exists: 'feature-branch'
```

In this example, if `feature-branch` exists, it will be checked out. If it doesn't exist, the action will default to the repository's default branch.

**Additional Information:**

For more details on the parameters and usage of the `actions/checkout` action, which is utilized within this composite action, please refer to the official GitHub Actions documentation: ([github.com](https://github.com/actions/checkout?utm_source=chatgpt.com))

This action is licensed under the Apache 2.0 License, allowing you to use, modify, and distribute it in your projects.

For any issues or contributions, please visit the [GitHub repository](https://github.com/PlentifulApp/checkout-if-exists). 
