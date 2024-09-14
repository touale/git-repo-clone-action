# Git Repository Clone Action

This GitHub Actions workflow allows you to clone a repository and check out a specific branch or tag. It is designed to
be reusable across different workflows and repositories.

## Inputs

### `repo_url`

- **Description**: The URL of the repository to clone.
- **Required**: `Yes`
- **Type**: `string`

### `branch`

- **Description**: The branch or tag to check out. If not specified, defaults to the branch or tag that triggered the
  workflow.
- **Required**: `No`
- **Type**: `string`

### `directory`

- **Description**: The directory where the repository should be cloned. Defaults to the current directory (`.`) if not
  specified.
- **Required**: `No`
- **Type**: `string`

### `list_files`

- **Description**: List all the files after checkout(optional)
  specified.
- **Required**: `No`
- **Type**: `boolean`
- **Default**: `false`

## Example Usage

You can call this reusable workflow from another workflow as follows:

```yaml

- name: setup ssh
  uses: ajaxer-org/ssh-setup-action@v1
  with:
    ssh-private-key: ${{ secrets.SSH_PRIVATE_KEY }}
    host: github.com
    ssh-key-filename: id_ed25519  # Can customize the key file name if needed

- name: Clone git repo
  uses: ajaxer-org/git-repo-clone-action@latest
  with:
    repo_url: 'git@github.com:ajaxer-org/git-repo-clone-action.git'
```