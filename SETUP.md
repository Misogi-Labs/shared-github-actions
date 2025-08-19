# Setup Instructions for Shared GitHub Actions

## 1. Create the Shared Actions Repository

1. Create a new repository (e.g., `your-org/shared-github-actions`)
2. Copy the contents of this `shared-github-actions/` folder to the new repository
3. Push to the repository and make it accessible to your organization

## 2. Update Repository References

In all your workflows that use the shared action, update the `uses` line:

```yaml
# Replace this placeholder:
uses: your-org/shared-github-actions/slack-notify@main

# With your actual organization and repository:
uses: misogi-org/shared-github-actions/slack-notify@main
```

## 3. Repository Secrets

Each repository using the shared action needs these secrets:

- `SLACK_WEBHOOK_URL` - Your Slack webhook URL for notifications

The shared action will automatically use the secrets from the calling repository.

## 4. Benefits

✅ **Centralized Management**: Update Slack notification logic in one place  
✅ **Version Control**: Pin to specific versions with `@v1.0` tags  
✅ **Consistent Formatting**: All repos use the same notification format  
✅ **Easy Testing**: Test changes in one place before rolling out  
✅ **Reduced Duplication**: No more copy-pasting workflow code  

## 5. Advanced Usage

### Pin to Specific Versions
```yaml
uses: your-org/shared-github-actions/slack-notify@v1.0
```

### Use Development Branch
```yaml
uses: your-org/shared-github-actions/slack-notify@dev
```

### Override Repository Name
```yaml
uses: your-org/shared-github-actions/slack-notify@main
with:
  repository-name: "Custom Name"
  # ... other inputs
```

## 6. Next Steps

1. Create the shared repository
2. Update the workflow files in your repos
3. Test the notifications
4. Consider creating more shared actions for other common workflows (CI, deployments, etc.)