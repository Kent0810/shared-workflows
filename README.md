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
    with:
      federation_rule_id: fdrl_...
      organization_id: <org UUID>
      service_account_id: svac_...
      # workspace_id: wrkspc_...   # only if the rule covers several workspaces
    permissions:
      contents: read
      pull-requests: write
      issues: write
      id-token: write
```

### Inputs

| Input | Required | Description |
|---|---|---|
| `federation_rule_id` | yes | Anthropic federation rule ID (`fdrl_...`) |
| `organization_id` | yes | Anthropic organization UUID |
| `service_account_id` | yes | Anthropic service account ID (`svac_...`) |
| `workspace_id` | no | Workspace ID (`wrkspc_...`), only needed if the rule covers several workspaces |
