# Github Actions Functions Explained | Build a Production - Style CI Pipeline

## Functions

Functions are built-in capabilities used within expressions (${{ }}) in process data, evaluate conditions, manipulate values, and make dynamic workflow execution decisions based on runtime information.

### General-Purpose Functions

_Purpose_ : Help workflows process data, evaluate conditions, manipulate values, work with structured data, and build dynamic automation logic during execution.

**Example** : contains(), startsWith(), endsWith(), format(), join(), hashFiles(), toJSON().

- _contains()_
  - if: ${{ contains(github.ref_name, 'release' )}}
  - true for branches like release/v1.0
- _startsWith()_
  - if: ${{ startsWith(github.ref_name, 'feature/' )}}
  - true for branches like feature/login
- _endsWith()_
  - if: ${{ endsWith(github.ref_name, '-prod' )}}
  - true for names ending with -prod
- _format()_
  - ${{ format('payment-service:{0}-{1}', github.ref_name, git) }}
  - Payment-service:feature-login-42
- _join()_
  - ${{ join(formJSON('["dev","qa","prod"]'),',') }}
  - dev, qa, prod

### Status Check Functions

_Purpose_ : Help workflows make execution decisions based on the success, failure, or cancellation status of previous jobs and steps.

- **Examples** : success(), failure(), always(), cancelled()

- _success()_
  - if: ${{ success() }}
  - true when all previous jobs or steps succeed
- _failure()_
  - if: ${{ failure() }}
  - true when any previous job or step fails
- _always()_
  - if: ${{ always() }}
  - true regardless of previous job or step outcome
- _cancelled()_
  - if: ${{ cancelled() }}
  - true when workflow execution is cancelled
