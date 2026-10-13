Sign in to GitHub. Your GitHub account has two-factor authentication turned on, so Git can't use your password. Instead, `gh` signs you in through the browser and stores a secure token that Git uses over **HTTPS**:

```bash
gh auth login --hostname github.com --git-protocol https --web
```

1. If it asks **"Authenticate Git with your GitHub credentials?"**, answer **Y**.
2. Copy the **one-time code** it shows (for example `ABCD-1234`), then press **Enter**.
3. A browser opens at `https://github.com/login/device`. If no browser opens, open that address yourself.
4. Paste the code, click **Continue**, and then **Authorize GitHub CLI**.
5. Back in the terminal, wait for **"Logged in as …"**.

<!-- SCREENSHOT: GitHub device activation page asking for the one-time code -->

Check that it worked:

```bash
gh auth status
```

You should see **"Logged in to github.com account *your-username*"** and **"Git operations protocol: https"**.
