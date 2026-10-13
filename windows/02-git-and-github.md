---
title: 2. Git and GitHub
---

All commands on this page go into the **Ubuntu** terminal.

## Step 1: Check Git

Ubuntu includes Git:

```bash
git --version
```

This should print a version such as `git version 2.x`. If it says `command not found`, install it with `sudo apt install -y git`.

## Step 2: Configure Git

```{include} ../_snippets/git-config.md
```

## Step 3: Install the GitHub CLI

Install `gh` from GitHub's official package repository. Copy the whole block and paste it as one command:

```bash
(type -p wget >/dev/null || (sudo apt update && sudo apt install wget -y)) \
	&& sudo mkdir -p -m 755 /etc/apt/keyrings \
	&& out=$(mktemp) && wget -nv -O$out https://cli.github.com/packages/githubcli-archive-keyring.gpg \
	&& cat $out | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
	&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
	&& sudo mkdir -p -m 755 /etc/apt/sources.list.d \
	&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
	&& sudo apt update \
	&& sudo apt install gh -y
```

This adds GitHub's signing key and package source to Ubuntu, then installs `gh`. Because it comes through `apt`, `sudo apt upgrade` keeps it up to date.

Check it:

```bash
gh --version
```

## Step 4: Sign in to GitHub

```{include} ../_snippets/gh-auth-login.md
```

:::{note} WSL and the browser
In WSL the browser may not open by itself. That's fine: open `https://github.com/login/device` in your Windows browser and enter the code there.
:::

```{include} ../_snippets/ssh-sidebar.md
```

Next: [](03-python-and-poetry.md).
