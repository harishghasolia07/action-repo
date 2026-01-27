# Action Repo

This repository is used to trigger GitHub webhook events for the [webhook-repo](https://github.com/yourusername/webhook-repo) application.

## Purpose

When you perform any of the following actions on this repository, GitHub will send a webhook event to the configured endpoint:

- **Push** - When code is pushed to any branch
- **Pull Request** - When a pull request is opened, reopened, or merged
- **Merge** - Automatically detected when a pull request is merged

## Setup Instructions

### 1. Configure the Webhook

1. Go to **Settings** → **Webhooks** → **Add webhook**
2. Fill in the details:

| Field | Value |
|-------|-------|
| Payload URL | `https://your-webhook-repo-url.com/webhook` |
| Content type | `application/json` |
| Secret | (optional) Your secret key |
| SSL verification | Enable (if using HTTPS) |

3. Under "Which events would you like to trigger this webhook?", select:
   - **Let me select individual events**
   - ✅ **Pushes**
   - ✅ **Pull requests**

4. Click **Add webhook**

### 2. Test the Webhook

After setup, GitHub will send a `ping` event. Check your webhook-repo logs to verify it was received.

Then try:

```bash
# Test a push
echo "test" >> test.txt
git add .
git commit -m "Test push event"
git push

# Test a pull request
git checkout -b test-pr-branch
echo "PR test" >> pr-test.txt
git add .
git commit -m "Test PR"
git push -u origin test-pr-branch
# Then create a PR on GitHub
```

## Related Repository

- [webhook-repo](https://github.com/yourusername/webhook-repo) - The Flask application that receives and displays webhook events

## License

MIT
