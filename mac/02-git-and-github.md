---
title: 2. Git and GitHub
---

## Step 1: Install Git and the GitHub CLI

```bash
brew install git gh
```

This installs current versions of Git and the GitHub CLI (`gh`).

## Step 2: Check that you're using Homebrew's Git

```bash
which git && git --version
```

`which git` should print `/opt/homebrew/bin/git` (Apple Silicon) or `/usr/local/bin/git` (Intel). If it prints `/usr/bin/git`, that's Apple's older copy, and your PATH isn't set up yet: close and reopen Terminal, then see [step 3 of the Homebrew page](#mac-homebrew-path).

## Step 3: Configure Git

```{include} ../_snippets/git-config.md
```

## Step 4: Sign in to GitHub

```{include} ../_snippets/gh-auth-login.md
```

```{include} ../_snippets/ssh-sidebar.md
```

Next: [](03-python-and-poetry.md).
