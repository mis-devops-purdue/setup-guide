---
title: 2. Git and GitHub
---

## Step 1: Check Git

Git is preinstalled:

```bash
git --version
```

## Step 2: Configure Git

```{include} ../_snippets/git-config.md
```

Your Git settings are saved in `~/.gitconfig`, inside your home folder, so they're kept between sessions.

## Step 3: Check for the GitHub CLI

```bash
gh --version
```

- If this prints a version (such as `gh version 2.x`), it's already installed. **Skip to step 5.**
- If it says `command not found`, do step 4.

## Step 4: Install the GitHub CLI in your home folder (only if needed)

You can't use `apt` here, because anything outside your home folder is erased when the session ends. Instead, download GitHub's official release into `~/.local/bin`. Run each command in order.

Find the latest version number:

```bash
GH_VERSION=$(curl -fsSLI -o /dev/null -w '%{url_effective}' https://github.com/cli/cli/releases/latest | sed 's#.*/v##') && echo "$GH_VERSION"
```

This asks GitHub for its latest release and prints the version, such as `2.102.0`.

Download and unpack it:

```bash
curl -fsSL "https://github.com/cli/cli/releases/download/v${GH_VERSION}/gh_${GH_VERSION}_linux_amd64.tar.gz" | tar -xz -C /tmp
```

Copy the `gh` program into your home folder:

```bash
mkdir -p ~/.local/bin && cp "/tmp/gh_${GH_VERSION}_linux_amd64/bin/gh" ~/.local/bin/
```

Check it:

```bash
gh --version
```

If this says `command not found`, make sure you did [step 5 on the previous page](#cloud-shell-path), then run `source ~/.bashrc`.

## Step 5: Sign in to GitHub

```{include} ../_snippets/gh-auth-login.md
```

:::{note} Cloud Shell and the browser
Cloud Shell can't open a browser for you. Open `https://github.com/login/device` in a new browser tab and enter the code there. `gh` saves its sign-in in your home folder, so it's kept between sessions.
:::

```{include} ../_snippets/ssh-sidebar.md
```

Next: [](03-python-and-poetry.md).
