## Why & What of Matrix Strategy

Unlike traditional workflows, where a job runs only once, Matrix Strategy allows Github Actions to automatically run the same job multiple times using different Matrix Values.

- Automatically creates one job for every Matrix Value or combination you define
- Every generated job runs the same workflows steps. but uses a different Matrix Value.
- Commonly used to test applications across different runtime versions, OS, Browsers, databases, cloud providers, and deployment environments.

_Example_

```bash
name: 01 - Matrix Strategy Workflows
on: workflow_dispatch

jobs:
  test-job:
    strategy:
      matrix:
        os: [ubuntu-latest, windows-latest, macos-latest]
        python-version: ["3.11", "3.12", "3.13"]
    runs-on: ${{ matrix.os }}
    steps:
      - name: SetUp Python
        uses: actions/setup-python@v6
        with:
          python-version: ${{ matrix.python-version }}
      - name: Run Tests
        run: pytest

```