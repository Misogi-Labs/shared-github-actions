# Shared GitHub Actions for Misogi Platform

This repository contains reusable GitHub Actions and workflows for the Misogi Platform projects.

## Actions

### slack-notify
Sends PR notifications to Slack with proper formatting and error handling.

**Usage:**
```yaml
- uses: your-org/shared-github-actions/slack-notify@main
  with:
    webhook-url: ${{ secrets.SLACK_WEBHOOK_URL }}
    pr-title: ${{ github.event.pull_request.title }}
    pr-author: ${{ github.event.pull_request.user.login }}
    pr-branch: ${{ github.event.pull_request.head.ref }}
    pr-target: ${{ github.event.pull_request.base.ref }}
    pr-url: ${{ github.event.pull_request.html_url }}
    pr-description: ${{ github.event.pull_request.body }}
    action-type: ${{ github.event.action }}
```

## Secret Management

Each repository using these shared actions maintains its own secrets:
- `SLACK_WEBHOOK_URL` - Your Slack webhook URL for notifications

The shared actions will use the secrets from the calling repository automatically.

## Repository Structure

```
shared-github-actions/
├── slack-notify/
│   └── action.yml
├── workflows/
│   └── examples/
│       └── pr-notification.yml
└── README.md
```