# GitHub Actions Outputs Explained | Step, Job & Reusable Workflow Outputs

## Output

Output are values generated during workflow execution and shared across steps, jobs, reusable workflows, or calling workflows.

**Step OutPuts**

- Used to pass values from one step to another step within the same job.
- _Example_ A deployment step generates a deployment URL that subsequent steps use for notifications or reporting.

_Example_

```bash
name: 01 - Steps Outputs

on: push

jobs:
  steps-job-output:
    runs-on: ubuntu-latest
    steps:
      - name: Generate Release Version
        id: version
        run: |
          echo "release_version=v1.0.0" >> $GITHUB_OUTPUT
      - name: Display Release Version
        run: |
          echo "${{steps.version.outputs}}"

```

---

**Job OutPuts**

- Used to pass values from one job to another job within the same workflow.
- _Example_ A deployment job generates a deployment URL that a notification job needs to send deployment notifications.

_Example_

```bash

```

---

**Reusable Workflow Outputs**

- Used to return values from a reusable workflows back to the calling workflows.
- _Example_ A centralized deployment workflow generates a deployment URL that the calling workflow uses for notifications, approvals, or reporting.

_Example_

```bash

```