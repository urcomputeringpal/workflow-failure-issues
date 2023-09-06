# workflow-failure-issues

## Setup

1. Copy [`.github/workflows/workflow-failure-issues-issue-template.md`](https://github.com/urcomputeringpal/workflow-failure-issues/blob/main/.github/workflows/workflow-failure-issues-issue-template.md) to your repo. Customize as needed.
1. Add the below workflow to your repo, maybe as `.github/workflows/workflow-failure-issues.yml`

```yaml
name: Workflow Failure Issues
on:
  workflow_run:
    workflows:
      # List your workflow's full name here
      - Your critical workflow
      # Add a template to customize the issue for each workflow.
      # For .github/your-critical-workflow.yml:
      #     .github/your-critical-workflow-issue-template.md
types:
      - completed
jobs:
  workflow-failure-issues:
    uses: urcomputeringpal/workflow-failure-issues/.github/workflows/workflow-failure-issues.yml@v0.0.1
    if: |
      (
        github.event_name == 'schedule' ||
        github.event.workflow_run.head_branch == github.event.repository.default_branch
      )
```
