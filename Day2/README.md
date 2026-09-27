# GitHub Actions Triggers & Runners Explained | Events, Contexts & Hosted Runners

A Trigger is an event or activity that starts workflow execution. Github Actions workflows remain Idle until triggered by configured events.

## Triggers

- Repository Events (push, pull_request, release, issues)
- Manual Triggers (Workflow_dispatch)
- Schedules Triggers (Schedule)
- External Trigger (repository_dispatch)
- Cross-Workflow Triggers (workflow_call)

**Repository Events (push, pull_request, release, issues)**

- Triggered automatically by repository activities
- _Foundation_ of CI and validation pipelines
- _UseCase_: PR validation and automated testing

```bash
on:
  push:
    branches:
      - main
```

**Manual Triggers (Workflow_dispatch)**

- Supports _controlled_ on-demand workflow execution
- Triggered using _UI, CLI, or API_
- _UseCase_: Production deployments and rollbacks

```bash
on:
    workflow_dispatch:

$ gh workflow run workflow.yaml
```

**Schedules Triggers (Schedule)**

- Executes workflows using POSIX Cron schedules
- Uses Github's best-effort scheduling model
- UseCase: Security scans and cleanup automation
- Example:

```bash
on:
  schedule:
    - cron: "*/5 * * * *"
```

**External Trigger (repository_dispatch)**

- Allows external system to trigger workflows
- Supports custom event payload integrations
- UseCase: monitoring and incident automation workflows

**Cross-Workflow Triggers (workflow_call)**

- Enables reusable workflow-based automation patterns
- Commonly used for centralized CI/CD logic
- UseCase: Organization-wide standardized pipelines

---

## There are 5 Types of Workflow Trigger

1. **Repository Event**
   - _push, pull_request, release, issues_
2. **Manual Trigger**
   - _workflow_dispatch_
3. **Scheduled Trigger**
   - _schedule_:
     - cron : "_/5 _ \* \* \*"
4. **External Trigger**
   - Custom event payload (repository_dispatch)
5. **Cross-Workflows Trigger**
   - _workflow_call_

---

## Context

```bash
name: "02 - Understanding Events"
on:
  workflow_dispatch:
  push:
  pull_request:
  schedule:
    - cron: "*/5 * * * *" # Runs every 5 Minutes
jobs:
  event-info-jobs:
    runs-on:
      steps:
        - name: Print Trigger Event
          run: echo "My Trigger is ${{ github.event_name}} event "

```

## Github Hosted Runners : Standers vs larger Runners
