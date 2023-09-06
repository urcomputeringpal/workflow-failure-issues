---
title: "{{ payload.workflow.name }} failed on {{ payload.workflow_run.head_branch }}"
labels:
- "{{ payload.workflow.name }}"
- actions
- failure
---

<!-- Please don't remove any of the labels from above. Doing so will result in tons of dupe issues. -->
<!-- See https://github.com/JasonEtco/create-an-issue for info about the interpolation supported. -->

{{ payload.workflow.name }} failed on a {{ payload.workflow_run.event }} event on {{ payload.workflow_run.head_branch }} at {{ payload.workflow_run.created_at }}

This workflow is using the default template for its failure notifications.
Create a new one to customize the message:

```
cd .github/workflows
wget https://raw.githubusercontent.com/urcomputeringpal/workflow-failure-issues/main/.github/workflows/workflow-failure-issues-issue-template.md
mv workflow-failure-issues-issue-template.md {{ env.WORKFLOW_TEMPLATE }}
# edit {{ env.WORKFLOW_TEMPLATE }}
```

Please include information about why failure of this workflow should schedule work.
For example, failures of the "Workflow Failure Issues" workflow indicate that work that has been previously determined to be important is not being scheduled.

-   {{ payload.workflow_run.html_url }}
-   {{ payload.workflow.html_url }}
