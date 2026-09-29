# GitHub Actions Inputs Explained | Workflow Inputs, Reusable Workflows & Production Use Cases

## Inputs

Inputs are parameters used to pass user-defined values into workflows, reusable workflows, or actions at runtime.

**Workflow Inputs**

- Used to provide values when triggering workflows using _workflow_dispatch_
- Example: Providing deployment parameters such as env, app version, or deployment strategy at runtime.

_Example_

```bash
name: 01 - Input Workflows
on:
  workflow_dispatch:
    inputs:
      environment:
        description: Deployment Environment
        required: true
        type: choice
        default: dev
        options:
          - dev
          - qa
          - prod
jobs:
  deploy-2:
    steps:
      - name: Printing Variable
        run: |
          echo "Deploying to ${{ inputs.environment }}"
```

---

**Reusable Workflow Inputs**

- Used to pass values from a calling workflow to a reusable workflow using workflow_call.
- _Example_ : Passing application name, replica count, or security to a centralized deployment workflow.

_Example_

```bash
#  Reusable Workflows

name: 01 - Input Workflows
on:
  workflow_dispatch:
    inputs:
      application_name:
        description: What will be the Application Name
        required: true
        type: string
      run_security_scan:
        description: Do you want to run Security Scan
        required: true
        type: boolean
      replicas:
        description: How many replica You want
        required: true
        type: number

# Calling Workflow

jobs:
  deploy:
    uses: ./.github/workflows/deploy.yaml
    with:
      application_name: payment-service
      run_security_scan: true
      replicas: 2
```

---

**Action Inputs**

- Used to pass values from a workflow to a custom action during execution.
- _Example:_ Providing an image name, Slack channel, or Terraform workspace to control action behavior.

Example: Github API Run and Github CLI Run

![Github API Run and Github CLI Run](./Api_Cli.png)

---

**Input Type In Github Actions**

- _string_
  - Free-from text input
- _choice_
  - Select from predefined values
- _boolean_
  - true/false selection
- _number_
  - numeric value
- _environment_
  - Select a Github Environment

---
