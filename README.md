# Git Repository Clone Action

This workflow is designed to clone a GitHub repository and check out a specific branch or tag. If no branch is
specified, it defaults to the branch or tag that triggered the workflow. If no directory is specified, it clones into
the current directory.

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

## Example Usage

You can call this reusable workflow from another workflow as follows:

```yaml
uses: ajaxer-org/git-repo-clone-action@latest
with:
  repo_url: 'git@github.com:ajaxer-org/git-repo-clone-action.git'
```