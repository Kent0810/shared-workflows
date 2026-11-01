# shared_workflow

Reusable GitHub Actions workflows.

## Claude Review

Runs Claude Code on a pull request and leaves short, to-the-point review comments.

### Usage

Add this to `.github/workflows/claude-review.yml` in your repo:

```yaml
name: Claude Review
on:
  pull_request:

jobs:
  review:
    uses: <owner>/shared_workflow/.github/workflows/claude-review.yml@main
    secrets:
      federation_rule_id: ${{ secrets.FEDERATION_RULE_ID }}
      organization_id: ${{ secrets.ORGANIZATION_ID }}
      service_account_id: ${{ secrets.SERVICE_ACCOUNT_ID }}
    # with:
    #   workspace_id: wrkspc_...   # only if the rule covers several workspaces
    permissions:
      contents: read
      pull-requests: write
      issues: write
      id-token: write
```

Store the three IDs as repository secrets (Settings → Secrets and variables → Actions).

### Secrets

| Secret | Required | Description |
|---|---|---|
| `federation_rule_id` | yes | Anthropic federation rule ID (`fdrl_...`) |
| `organization_id` | yes | Anthropic organization UUID |
| `service_account_id` | yes | Anthropic service account ID (`svac_...`) |

### Inputs

| Input | Required | Description |
|---|---|---|
| `workspace_id` | no | Workspace ID (`wrkspc_...`), only needed if the rule covers several workspaces |
