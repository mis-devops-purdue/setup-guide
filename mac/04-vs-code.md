---
title: 4. VS Code
---

## Step 1: Install VS Code

```bash
brew install --cask visual-studio-code
```

This installs VS Code into your **Applications** folder.

## Step 2: Open VS Code once

Open **Visual Studio Code** from Applications (or with **Cmd+Space**). If macOS warns that it was downloaded from the internet, click **Open**. Then close it.

<!-- SCREENSHOT: macOS "Visual Studio Code is an app downloaded from the Internet" dialog -->

## Step 3: Confirm `code` is on your PATH

```bash
which code
```

This should print a path ending in `/bin/code`. Homebrew sets up the `code` command for you.

If it prints nothing, open VS Code, press **Cmd+Shift+P**, type `shell command`, choose **Shell Command: Install 'code' command in PATH**, and then close and reopen Terminal.

## Step 4: Install the course extensions

Run each line:

```bash
code --install-extension ms-python.python
```

```bash
code --install-extension tamasfe.even-better-toml
```

These install the **Python** extension (running, debugging, and linting Python) and **Even Better TOML** (for Poetry's `pyproject.toml` files).

## Step 5: Create a projects folder and open it

```bash
mkdir -p ~/projects && cd ~/projects && code .
```

This creates a `projects` folder in your home folder and opens it in VS Code. If VS Code asks whether you trust the authors of the files in this folder, click **Yes, I trust the authors**.

In VS Code, press **Ctrl+`** (Control and the backtick key) to open a terminal inside VS Code. You can use it for everything in this course.

Next: [](05-gcloud.md).
