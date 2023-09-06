# workflow-failure-issues

- Creates issues like https://github.com/urcomputeringpal/workflow-failure-issues/issues/8 when critical workflows fails on the default branch.
- Closes them when the workflow passes.
- Supports per-workflow issue templates.

## Setup

Add the below workflow to your repo, maybe as `.github/workflows/workflow-failure-issues.yml`

```yaml
name: Workflow Failure Issues
on:
  workflow_run:
    workflows:
      # List your workflow's full name here
      - Your critical workflow
    types:
      - completed
jobs:
  workflow-failure-issues:
    uses: urcomputeringpal/workflow-failure-issues/.github/workflows/workflow-failure-issues.yml@v0.0.5
    if: |
      (
        github.event_name == 'schedule' ||
        github.event.workflow_run.head_branch == github.event.repository.default_branch
      )
```
