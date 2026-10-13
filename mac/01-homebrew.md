---
title: 1. Homebrew
---

## Step 1: Open Terminal

Press **Cmd+Space**, type `Terminal`, and press **Enter**.

## Step 2: Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

This downloads and runs Homebrew's official installer.

- When it asks for your **Password**, type your Mac login password. Nothing appears while you type; that's normal. Press **Enter**.
- Press **Enter** again when it asks you to continue.
- If Apple's **Command Line Tools** aren't installed yet, the installer installs them first. This can take 10 minutes or more.

<!-- SCREENSHOT: Terminal showing the Homebrew installer's "Next steps" section -->

(mac-homebrew-path)=
## Step 3: Add Homebrew to your PATH (Apple Silicon only)

When the installer finishes, it prints a **Next steps** section. On an Apple Silicon Mac, run these three commands (they're the same ones it prints):

```bash
echo >> ~/.zprofile
```

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv zsh)"' >> ~/.zprofile
```

```bash
eval "$(/opt/homebrew/bin/brew shellenv zsh)"
```

The first two save the setting so every new Terminal finds Homebrew; the third applies it to this one.

On an **Intel** Mac, skip this step: Homebrew is in `/usr/local/bin`, which is already on your PATH.

## Step 4: Check Homebrew

```bash
brew --version
```

This should print `Homebrew` followed by a version number. If it says `command not found`, close Terminal, open it again, and retry. If it still fails, see [](#command-not-found).

Next: [](02-git-and-github.md).
