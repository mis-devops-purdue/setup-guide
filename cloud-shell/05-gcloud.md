---
title: 5. Google Cloud CLI
---

The Google Cloud CLI is preinstalled in Cloud Shell, and you're already signed in with the account you used to open it.

```{include} ../_snippets/gcloud-no-billing.md
```

## Step 1: Check the CLI

```bash
gcloud --version
```

## Step 2: Check your account

```bash
gcloud auth list
```

Your course Google account should be listed with an asterisk (`*`) marking it as **ACTIVE**. If Cloud Shell shows an **Authorize Cloud Shell** pop-up, click **Authorize**.

<!-- SCREENSHOT: Cloud Shell "Authorize Cloud Shell" pop-up -->

If no account is listed, or the wrong one is active, run:

```bash
gcloud auth login
```

Open the link it prints in a new tab, choose your course account, and paste the code Google shows you back into the terminal.

Part 3 is done. Next: [](../verify.md).
