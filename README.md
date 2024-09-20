# Git Repository Clone and Commit Action

This GitHub Action allows you to clone a GitHub repository, check out a specific branch or tag, configure Git user
settings, and sign commits/tags using an SSH key. It's designed to streamline the process of managing repositories in
automated workflows.

## Features

- Clone a GitHub repository using SSH.
- Check out a specific branch or tag.
- Configure Git user.name and user.email for commits.
- Optionally sign commits and tags using an SSH key.
- List the contents of the cloned repository.

## Inputs

| Input             | Description                                        | Required | Default                |
|-------------------|----------------------------------------------------|----------|------------------------|
| `repo_url`        | The Git repository SSH URL to clone.               | Yes      |                        |
| `ssh_private_key` | The SSH private key to access the repository.      | Yes      |                        |
| `directory`       | The directory to clone the repository into.        | No       | Current directory name |
| `ref`             | The branch or tag to checkout.                     | No       |                        |
| `list_files`      | List all the files after checkout.                 | No       | `false`                |
| `user_name`       | The Git user name for later commits.               | No       | `GitHub Actions`       |
| `user_email`      | The Git user email for later commits.              | No       | `actions@github.com`   |
| `sign_commit`     | Whether to sign commits and tags with the SSH key. | No       | `true`                 |

## Usage

```yaml
name: Example Workflow

on: [push]

jobs:
  clone-and-commit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2
      
      - name: Git Repository Clone and Commit Action
        uses: ajaxer-org/ajaxer-org/git-repo-clone-action@latest
        with:
          repo_url: 'git@github.com:your-username/your-repo.git'
          ssh_private_key: ${{ secrets.SSH_PRIVATE_KEY }}
          directory: 'your-directory'
          ref: 'main'
          list_files: 'true'
          user_name: 'Your Name'
          user_email: 'your-email@example.com'
          sign_commit: 'true'
```