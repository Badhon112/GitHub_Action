# GitHub Actions Triggers & Runners Explained | Events, Contexts & Hosted Runners

A Trigger is an event or activity that starts workflow execution. Github Actions workflows remain Idle until triggered by configured events.

## Triggers

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
