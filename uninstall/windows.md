---
title: Uninstall on Windows (WSL)
---

Do [](index.md) first: save your work and sign out.

Choose **one** option:

- **Option A: remove the course tools only.** Keeps Ubuntu and WSL, and anything else you've installed in them.
- **Option B: remove everything.** Deletes Ubuntu and every file in it, and uninstalls VS Code. Use this if you don't use WSL for anything else.

## Option A: Remove the course tools only

Run these commands in the **Ubuntu** terminal unless the step says otherwise. They undo the setup in reverse order.

### A1: Remove the Google Cloud CLI

```bash
sudo apt-get remove -y google-cloud-cli
```

Remove Google's package source and signing key, so `apt` stops checking them:

```bash
sudo rm -f /etc/apt/sources.list.d/google-cloud-sdk.list /usr/share/keyrings/cloud.google.gpg
```

Remove your `gcloud` settings:

```bash
rm -rf ~/.config/gcloud
```

### A2: Remove the VS Code extensions

```bash
code --uninstall-extension ms-python.python
```

```bash
code --uninstall-extension tamasfe.even-better-toml
```

These remove the extensions from inside WSL. If `code` isn't found, skip this step; Option B removes them anyway.

### A3: Remove Poetry and pipx

```bash
pipx uninstall poetry
```

This removes Poetry and its export plugin together.

Remove Poetry's settings and download cache:

```bash
rm -rf ~/.config/pypoetry ~/.cache/pypoetry
```

Remove pipx:

```bash
sudo apt remove -y pipx
```

`pipx ensurepath` added a line to your shell's startup file (usually `~/.bashrc`) that puts `~/.local/bin` on your PATH. It's harmless to leave.

### A4: Remove the GitHub CLI

```bash
sudo apt remove -y gh
```

Remove GitHub's package source and signing key:

```bash
sudo rm -f /etc/apt/sources.list.d/github-cli.list /etc/apt/keyrings/githubcli-archive-keyring.gpg
```

Remove `gh`'s settings:

```bash
rm -rf ~/.config/gh
```

### A5: Remove your Git settings

```bash
git config --global --unset user.name
```

```bash
git config --global --unset user.email
```

```bash
git config --global --unset init.defaultBranch
```

Git itself came with Ubuntu, so leave it installed.

### A6: Clean up

```bash
sudo apt autoremove -y && sudo apt update
```

This removes packages that were only installed to support the tools above, then refreshes the package list without the removed sources.

### A7: Remove the course files (optional)

:::{danger} This deletes your course work
Only run this after you've pushed everything you want to keep (see [](index.md)).
:::

```bash
rm -rf ~/projects ~/verify-setup
```

If you also want to uninstall VS Code from Windows, do [step B3](#uninstall-windows-vscode).

## Option B: Remove everything

### B1: Delete Ubuntu

:::{danger} This permanently deletes Ubuntu and every file in it
Everything inside Ubuntu is erased: your `~/projects` folder, the tools you installed, and your settings. It can't be undone. Make sure your work is pushed to GitHub first.
:::

In **PowerShell**:

```powershell
wsl --unregister Ubuntu
```

Check that it's gone:

```powershell
wsl -l -v
```

Ubuntu should no longer be listed.

### B2: Uninstall WSL (optional)

Only do this if no other Linux distribution is listed and you don't use WSL for anything else. Open **Settings → Apps → Installed apps**, find **Windows Subsystem for Linux**, click **⋯**, and choose **Uninstall**. If **Ubuntu** is also listed there, uninstall it the same way.

<!-- SCREENSHOT: Windows Settings > Installed apps showing Windows Subsystem for Linux with the Uninstall menu -->

(uninstall-windows-vscode)=
### B3: Uninstall VS Code

Open **Settings → Apps → Installed apps**, find **Microsoft Visual Studio Code**, click **⋯**, and choose **Uninstall**.

To also remove VS Code's settings and extensions, delete these two folders in File Explorer (paste each path into the address bar):

- `%APPDATA%\Code`
- `%USERPROFILE%\.vscode`
