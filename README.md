# GitHub Actions Workflows

This repository hosts **reusable workflows** for GitHub repositories in the organization.

## 🚀 `issue-notifier.yml`

Use this workflow to send email notifications when:

- An issue is opened or assigned → email sent to the assignee
- An issue is closed → email sent to a fixed helpdesk address

### 🔧 How to Use in Your Repo

1. Create a workflow in your repo:

`.github/workflows/trigger-issue-notifier.yml`

```yaml
name: Trigger Issue Notifier

on:
  issues:
    types: [opened, closed, assigned]

jobs:
  call-notifier:
    uses: Mitra-Dev/github-actions-workflows/.github/workflows/issue-notifier.yml@main
    secrets:
      OUTLOOK_EMAIL: ${{ secrets.OUTLOOK_EMAIL }}
      OUTLOOK_APP_PASSWORD: ${{ secrets.OUTLOOK_APP_PASSWORD }}
    with:
      helpdesk_email: apps@mitra.mw
