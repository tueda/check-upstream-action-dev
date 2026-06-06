# check-upstream-action

This action checks whether upstream changes can be merged cleanly
into the current branch.
If the changes can be merged without conflicts, it opens a pull request.
If conflicts are detected, it creates or updates an issue.

> [!WARNING]
> This is a development version and may be changed, archived, or removed
> after a stable version is released.

## Usage

```yaml
name: Check upstream

on:
  schedule:
    - cron: '0 0 * * *'  # Runs daily at 00:00 UTC.
  workflow_dispatch:

permissions:
  contents: write
  pull-requests: write
  issues: write

jobs:
  check-upstream:
    runs-on: ubuntu-latest
    steps:
      - uses: tueda/check-upstream-action-dev@main
        with:
          upstream-repository: owner/repository
```

Run this workflow on the branch you want to update with upstream changes.
Add a branch condition to the job or workflow if needed.

For all available inputs and their defaults, see [`action.yml`](action.yml).
