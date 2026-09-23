## What is Github Actions?

- Github Actions is a continuous integration and continuous delivery (CI/CD) platform built directly into github

- It allows you to automate various tasks within your software development workflow

## Github Actions: Components

- Workflows
- Jobs
- Events
- Actions
- Runners

- _Workflows_
  - A workflow is a configurable automated process that will run one or more jobs
  - Workflows are defined in .github/workflows directory in a repository
  - Workflows are defined by a YAML File

- _Jobs_
  - A job is a set of steps in a workflow that is executes on the same runner.
  - Each step is either a shell script that will be executed, or an action that will be run
  - Steps are executed in order and are dependent on each other

- _Events_
  - An Events is a specific activity in a repository that trigger a workflow run.
  - For Example, activity can originate from Github when someone creates a pull request, opens an issue, or pushes a commit to a repository

- _Actions_
  - An actions is a custom application for the Github Actions platform that performs a complex but frequently repeated task
  - Use an action to help reduce the amount of repetitive code that you write in your workflow files

- _Runners_
  - A runner is a server that runs your workflows when they're triggered, Each runner can run a single job at a time
  - Github provides gitHosted runners also we can create self hosted runners to tun our workflows

---

## Simple Workflow Structure

- _Workflow1_
  - Job : A job could be build job, deploy job
    - Steps : Run a command
    - Steps : Upload Docker Image TO

---

## Creating Multiple Jobs in a single Workflow

```bash
name: Hello World
on: workflow_dispatch

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Build Step
        run: |
          echo "A Demo Build"

  test:
    runs-on: ubuntu-latest
    steps:
      - name: Test Step
        run: |
          echo "Running a Build Test"

```

## Executing Jobs in Parallel and Sequentially

```bash
name: Hello World
on: workflow_dispatch

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Build Step
        run: |
          echo "A Demo Build"

  test:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Test Step
        run: |
          echo "Running a Build Test"
  deploy:
    runs-on: ubuntu-latest
    needs: test
    steps:
      - name: Deploy Step
        run: |
          echo "Running a Deploy Stage"

```

---

## Github Actions Workflow Triggers & Types

**Types of Triggers**

1. Event-based triggers
2. Manual triggers
3. Scheduled triggers
4. Workflow Triggers

- **Push and Pull_Request triggers**

```bash

name: Hello World
on:
  push:
    branches:
      - main
```