---
title: Verify your setup
---

Everyone finishes here, whichever part you followed. A short script checks your setup and prints a summary for you to screenshot for **Prep 2 – Setup**.

:::{note} The script only reads
It checks what's installed and how it's configured. It **never** installs, changes, or deletes anything, and it never asks for your password. You can read exactly what it does in its repository: [mis-devops-purdue/verify-setup](https://github.com/mis-devops-purdue/verify-setup). Checking a script before you run it is a good habit.
:::

## Step 1: Open your terminal and go home

Use the terminal from your part: **Ubuntu** (Windows), **Terminal** (Mac), or the **Cloud Shell** terminal.

```bash
cd ~
```

On Windows, this matters: run the script from your Linux home folder, not from somewhere under `/mnt/c`.

## Step 2: Download the script

```bash
gh repo clone mis-devops-purdue/verify-setup
```

This copies the script's repository to a `verify-setup` folder in your home folder. If this works, your GitHub sign-in works too.

If you've cloned it before, get the latest version instead:

```bash
git -C ~/verify-setup pull
```

## Step 3: Run it

```bash
bash verify-setup/verify.sh
```

Each line shows ✅ (passed), ❌ (failed), or ⚠️ (a warning). Every ❌ comes with a one-line fix and the page of this guide to revisit.

## Step 4: Fix anything marked ❌ and run it again

Fix each problem, **close and reopen your terminal**, and run step 3 again. Repeat until the summary shows **0 failed**. The table below covers the most common problems.

## Step 5: Take a screenshot and submit it

When everything passes, take a screenshot of the **summary box** at the bottom of the output:

- **Windows:** press **Windows key + Shift + S** and drag around the box.
- **Mac:** press **Cmd + Shift + 4** and drag around the box.

Make sure the screenshot shows your platform, the date and time, your GitHub username, your Google account, and the PASS/FAIL count. Submit it to **Prep 2 – Setup** on Brightspace.

<!-- SCREENSHOT: verify.sh summary box showing all checks passed -->

## Troubleshooting

| What the script says | What to do |
| --- | --- |
| ❌ running on Windows outside WSL | You ran it in PowerShell or Git Bash. Open **Ubuntu** and run it there ([](windows/01-install-wsl.md)). |
| `gh: command not found` when cloning | Install `gh` (page 2 of your part), then close and reopen your terminal. |
| Cloning asks for a username or password | `gh` isn't signed in, or Git isn't using it. Run `gh auth login --hostname github.com --git-protocol https --web` again, then `gh auth setup-git`. |
| ❌ `user.name` / `user.email` not set | Repeat the Git configuration step on page 2 of your part. |
| ❌ `gh auth status` failed | Run `gh auth login --hostname github.com --git-protocol https --web`. |
| ❌ Python older than 3.11 | See [](#python-too-old). |
| ❌ `pipx` not found | Run `pipx ensurepath`, then close and reopen your terminal. |
| ❌ `poetry` not found | Close and reopen your terminal. If it's still missing, repeat page 3 of your part. |
| ❌ export plugin missing | Repeat the export-plugin step on page 3 of your part (`pipx inject …` on Windows/Mac, `poetry self add …` in Cloud Shell). |
| ❌ `virtualenvs.in-project` not true | Run `poetry config virtualenvs.in-project true`. |
| ❌ `code` not found or extensions missing | Repeat page 4 of your part. On Windows, run the extension installs from **Ubuntu**, not PowerShell. |
| ⚠️ current folder is under `/mnt/c` | Run `cd ~` and run the script again. Keep your projects under `~/projects`. |
| ❌ no active `gcloud` account | Run `gcloud auth login` (page 5 of your part). |
| Something else | See [](troubleshooting.md), then contact the instructor or TA. Include a screenshot of the full script output. |

When the summary shows 0 failed, go to [](stop-here.md).
