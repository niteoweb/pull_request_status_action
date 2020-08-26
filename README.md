# Pull Request Status Action

[![CircleCI](https://circleci.com/gh/niteoweb/pull_request_status_action/tree/master.svg?style=svg)](https://circleci.com/gh/niteoweb/pull_request_status_action)
[![GitHub marketplace](https://img.shields.io/badge/marketplace-heroku--pull--request--status--action-blue?style=flat-square&logo=github)](https://github.com/marketplace/actions/pull-request-status-action)

A Github Action that creates a `Status` for the Pull Request.

## Usage

```yaml

jobs:
  update-pr-status:
    runs-on: ubuntu-latest
    steps:
    - name: Set PR Status to pending
        uses: niteoweb/pull_request_status_action@v1.0.0
        with:
          # Pull Request number (Mandatory)
          pr_number: 32

          # State to apply (Mandatory)
          # Any of the (error | failure | pending | success) states
          state: pending

          # Name of the repository in {organization}/{repo_name} format (Mandatory)
          repository: niteoweb/the-awesome-repo

          # Name to identify the Status (Optional)
          # Defaults to `default`
          context: default

        env:
          # Default Github Token
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

> `GITHUB_TOKEN` is required to communicate with Github Deployment API. Default token provided by Github can be used.

## Local Development

- Create a Python virtual environment(version > 3.6).
- Activate the environment.
- Install the development dependencies:

```bash
    pip install -r requirements-dev.txt
```

- Make changes.
- Test the changes:

```bash
    make tests
```

- Make sure that coverage is 100%.
