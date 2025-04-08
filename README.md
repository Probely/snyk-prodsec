# GitHub Workflow Actions

## Secrets-Scanning

```yml
name: Detect Secrets
on:
  pull_request:
  push:
  workflow_dispatch:
  schedule:
    - cron: "0 0 * * 0"
jobs:
  secrets-scan:
    uses: probely/snyk-prodsec/.github/workflows/secrets-scanning.yml@main
    with:
      channel: <team-slack-alerts-channel>
    secrets:
      SLACK_BOT_TOKEN: ${{ secrets.SLACK_SECRET }}
      GITLEAKS_LICENSE: ${{ secrets.GITLEAKS_LICENSE }}
```

### Parameters

- `channel`: the Slack channel where alerts will be sent

### Secrets

- `SLACK_BOT_TOKEN`: the token for the application (bot) that will be used to post slack messages
- `GITLEAKS_LICENSE`: the Gitleaks license. This is configured by ProdSec at organisation level

See [Events that Trigger Workflows](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#schedule) for running the worklfow on a schedule.