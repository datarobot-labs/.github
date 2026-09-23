# DataRobot Labs Org Profile

Org-level defaults for the [@datarobot-labs](https://github.com/datarobot-labs) GitHub organization. No application code lives here.

| Path | What it is |
| --- | --- |
| `profile/README.md` | The org profile page rendered at <https://github.com/datarobot-labs>. Public and indexed, and the first thing most people see. |
| `.github/workflows/` | Org-level reusable workflows that repos in this org call. |

## Review Router

[`review-router`](https://github.com/datarobot-oss/review-router) routes pull requests to the right reviewers based on `CODEOWNERS`, and notifies Slack and Jira. This repo holds the org-wide reusable workflow, so repos that opt in need one small file and no secrets of their own.

### Opting a repository in

Add `.github/workflows/review-router.yml` to the repository:

```yaml
name: Review Router

# SECURITY: this workflow uses pull_request_target, not pull_request, because
# review-router never checks out or executes PR code. Do not add actions/checkout
# or shell run: blocks to the caller.
# https://github.com/datarobot-oss/review-router/blob/main/docs/security/pull-request-target.md

on:
  pull_request_target:
    types: [labeled, opened, closed]
  pull_request_review:
    types: [submitted]
  pull_request_review_comment:
    types: [created]
  issue_comment:
    types: [created]

jobs:
  route:
    uses: datarobot-labs/.github/.github/workflows/review-router.yml@main
    secrets: inherit
```

Then add `.github/CODEOWNERS` to the same repository, on the default branch. The router reads it from the PR's base branch, so it has to be merged before routing works.

```
* @datarobot-labs/labs
```

### What the org owns

Opting a repo in assumes three things are already true at the org level:

1. The [`datarobot-pr-review-router`](https://github.com/apps/datarobot-pr-review-router) GitHub App is installed on `datarobot-labs`.
2. This repo carries the `REVIEW_ROUTER_*` Actions secrets, which callers pick up through `secrets: inherit`.
3. [`datarobot/.review-router-config`](https://github.com/datarobot/.review-router-config) has a `datarobot-labs` section under `orgs:`, mapping team slugs to labels and Slack channels. Without it the action logs a warning and falls back to its bundled config.

Upgrading the action for every repo in the org is a one-line change to the version pin in `.github/workflows/review-router.yml` here. Downstream repos pick it up on their next run.

Full documentation: [setup guides](https://github.com/datarobot-oss/review-router/tree/main/docs/setup).
