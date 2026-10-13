---
title: 5. Google Cloud CLI
---

```{include} ../_snippets/gcloud-no-billing.md
```

## Step 1: Install the Google Cloud CLI

```bash
brew install --cask gcloud-cli
```

This installs the Google Cloud CLI and puts `gcloud` on your PATH.

Check it:

```bash
gcloud --version
```

If it says `command not found`, close and reopen Terminal and try again.

## Step 2: Sign in

Sign in with the Google account you'll use for this course. See {{GCP_ACCOUNT_INSTRUCTIONS_URL}} for which account to use.

```bash
gcloud auth login
```

Your browser opens. Choose your account and click **Allow**. When the browser says you're authenticated, return to Terminal.

<!-- SCREENSHOT: Google "Google Cloud SDK wants to access your Google Account" consent page -->

Check that it worked:

```bash
gcloud auth list
```

Your account should be listed with an asterisk (`*`) marking it as **ACTIVE**. A message that no project is set is expected for now.

Part 2 is done. Next: [](../verify.md).
