# brianespinosa/actions

Reusable GitHub workflows

See GitHub's ["Reusing Workflows"](https://docs.github.com/en/actions/using-workflows/reusing-workflows) documentation for more information on how to reduce duplication and reuse workflows between repositories.

## Available Workflows

### [dependabot-pr-review.yml](.github/workflows/dependabot-pr-review.yml)

This action will add one approval to a PR and will mark it to auto-merge for any PRs that have been opened by the Dependabot user.

This requires:

1. Branch protection to be set on the `main` branch with some level of CI
2. Repository enabled with auto-merge functionality
3. Elevated [permissions from the calling workflow](https://docs.github.com/en/actions/using-workflows/reusing-workflows#supported-keywords-for-jobs-that-call-a-reusable-workflow)
4. [Needs to pass `secrets: inherit`](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idsecretsinherit) to the job for the `GITHUB_TOKEN`

#### Usage

```yml
name: Review and auto-merge Dependabot PRs

on: pull_request_target

jobs:
  dependabot-pr-review:
    permissions:
      pull-requests: write
      contents: write
    uses: brianespinosa/actions/.github/workflows/dependabot-pr-review.yml
    secrets: inherit
```
