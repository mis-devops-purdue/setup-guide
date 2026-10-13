---
title: 5. Google Cloud CLI
---

All commands on this page go into the **Ubuntu** terminal.

```{include} ../_snippets/gcloud-no-billing.md
```

## Step 1: Install the prerequisites

```bash
sudo apt-get update && sudo apt-get install -y apt-transport-https ca-certificates gnupg curl
```

This installs the tools `apt` needs to download and verify packages from Google.

## Step 2: Add Google's signing key

```bash
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg
```

This saves the key Ubuntu uses to check that Google's packages are genuine. If it asks whether to overwrite an existing file, answer **y**.

## Step 3: Add Google's package source

```bash
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee /etc/apt/sources.list.d/google-cloud-sdk.list
```

This tells `apt` where to download the Google Cloud CLI from.

## Step 4: Install the Google Cloud CLI

```bash
sudo apt-get update && sudo apt-get install -y google-cloud-cli
```

Check it:

```bash
gcloud --version
```

## Step 5: Sign in

Sign in with the Google account you'll use for this course. See {{GCP_ACCOUNT_INSTRUCTIONS_URL}} for which account to use.

```bash
gcloud auth login
```

This prints a long sign-in link and tries to open your browser.

- If your Windows browser opens, choose your account and click **Allow**.
- If nothing opens, hold **Ctrl** and click the link in the terminal (or copy it into your Windows browser).
- If the browser says it **can't reach `localhost`**, press **Ctrl+C** in the terminal and run `gcloud auth login --no-launch-browser` instead. Open the link it prints, sign in, and paste the code Google shows you back into the terminal.

<!-- SCREENSHOT: Google "Google Cloud SDK wants to access your Google Account" consent page -->

Check that it worked:

```bash
gcloud auth list
```

Your account should be listed with an asterisk (`*`) marking it as **ACTIVE**. A message that no project is set is expected for now.

Part 1 is done. Next: [](../verify.md).
