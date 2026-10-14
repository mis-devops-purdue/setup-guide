---
title: Before you uninstall
---

Use this section when you no longer need the course setup, for example at the end of the course, or when you want to remove a broken setup and start over.

:::{warning} Only uninstall when you're sure
Removing the course tools mid-semester means repeating this guide before the next class. If something is broken, try [](../troubleshooting.md) first, or contact the instructor or TA.
:::

## Step 1: Save your work

Uninstalling can delete files on your computer. Before you start, make sure everything you want to keep is **committed and pushed to GitHub**. For each project folder under `~/projects`:

```bash
git status
```

If it lists changed files or says your branch is **ahead of 'origin/main'**, commit and push before going further.

## Step 2: Sign out

Remove the sign-in tokens the course tools stored on your computer. Run these in the same terminal you used for setup (Ubuntu, Terminal, or Cloud Shell).

Sign out of GitHub:

```bash
gh auth logout --hostname github.com
```

Sign out of Google Cloud:

```bash
gcloud auth revoke --all
```

:::{tip} Revoke access on GitHub too (optional)
Signing out deletes the token from your computer. To also cancel it on GitHub's side, go to **GitHub → Settings → Applications → Authorized OAuth Apps**, click **GitHub CLI**, and click **Revoke**.
:::

## Step 3: Follow the page for your platform

| You set up | Go to |
| --- | --- |
| Part 1: Windows (WSL) | [](windows.md) |
| Part 2: Mac | [](mac.md) |
| Part 3: GCP Cloud Shell | [](cloud-shell.md) |

The Windows and Mac pages give you two options: remove **only the course tools**, or remove **everything** this guide installed. The Cloud Shell page resets Cloud Shell to how it was the first time you opened it.
