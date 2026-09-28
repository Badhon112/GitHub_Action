## Github Actions Workflows Logic Explained | Filters, Context, Variables & Expressions

**Refining Workflow Trigger Behavior**

- _Event Filters_
  - Control Under what conditions workflows execute
  - Help reduce unnecessary workflow executions
  - Commonly used filters : branches, paths, tags, ignore filters
  - Commonly used for : branch control, selective CI execution, monorepo optimization

```bash
on:
    push:
        branches:
            - "develop"
            - "release/*"
        paths:
            - "app/**"
            - "docker/**"
            - ".github/workflows/**"
```

```bash
on:
    push:
        branches-ignore:
            - "experimental/*"
            - "temp/*"
        paths-ignore:
            - "**/*.md"
            - "docs/**"
```

- _Activity Types_
  - Control which operation within an event triggers workflows
  - Help improve workflow execution precision
  - Commonly used with: pull_request, issues, release events
  - Common Examples : opened, synchronize, reopened

```bash
on:
    pull_request:
        types:
            - opened
            - synchronize
            - reopened
            - closed
            - ready_for_review
        branches:
            - main
```
