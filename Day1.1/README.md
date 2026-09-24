## What is Github Actions?

Github native event-driven automation and orchestration platform for modern software delivery workflows.

- Managed service maintained and scaled by Github
- Deeply integrated with the Github ecosystem
- Automation pipeline (Workflows) are defined using YAML

## Advantages of Platform-Native CI-CD

- No separate CI/CD server setup and management
- Native repository authentication and permissions integration
- Workflows triggered directly using repository events
- Unified platform for code, PRs, and automation
- Managed runners reduce CI/CD infrastructure overhead

## Advantages Specific to Github Actions

- Massive Github developer ecosystem adoption
- Large reusable Github MarketPlace actions ecosystem
- Strong open-source ecosystem and community support

---

## Core Constructs of Github Actions

**_Workflow_**

- Top-level automation definition inside Github Actions
- Defines Triggers using Github repository events
- Contains one or more executable jobs
- Stores under _.github/workflows/_ inside repositories

**_Jobs_**

- Logical execution stages inside a workflow
- Each job executes on an independent runner
- Jobs execute in parallel by default
- Supports dependencies using the needs keyword

If you have worked with Jenkins before, you can roughly think of:

- Workflows as pipelines
- jobs as stages
- steps as individual operations inside stages

**_Steps_**

- Smallest executable units inside Github Actions Jobs
- Perform actual operational and automation tasks
- Execute sequentially within the same runner env
- Commonly use run and uses keywords

**_Runner_**

- Execution environment responsible for running workflow Jobs
- Receive Jobs, Execute steps and return execution status
- It's like a agent in jenkins, that work all the leg work

**Example**:

```bash
name: My First WorkFlow
on: push
jobs:
  job-1:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        run: echo "Hello World From Step 1"
      - name: Step 2
        run: echo "Hello World From Step 2"
  job-2:
    runs-on: ubuntu-latest
    steps:
      - name: Final Step
        run: echo "Job 2 executed after Job 2"

```

---

## Runner Types in Github Actions

While workflows, jobs and steps define the automation logic, the actual execution is performed by runners

**Github Hosted Runners (Managed by Github)**

- Fresh ephemeral execution envs provisioned for each job
- No patching, scaling, or infra maintenance required
- Limited infra and networking customization capabilities
- Example : Ubuntu-latest, windows-latest, macos-latest

**Self-Hosted Runners (managed by You/Organization)**

- Jobs may execute on persistent runner envs
- Organizations manage patching, scaling, and lifecycle operations
- Supports private networking and deep env customization
- Example: AWS EC2, Kubernetes, on-prem servers, Azure VMs.

Most production organization use a hybrid runner strategy where standard CI/CD workloads execute on Github-Hosted runners, While security-sensitive, compliance-controlled, private-network, GPU-based, or highly customized workloads execute on self-hosted runners.

---

# DEMO

```bash
name: My First WorkFlow
on: push
jobs:
  job-1:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        run: echo "Hello World From Step 1"
      - name: Step 2
        run: echo "Hello World From Step 2"
  job-2:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        run: echo "Job 2 executed after Job 2"

```