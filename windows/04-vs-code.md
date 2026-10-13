---
title: 4. VS Code
---

VS Code is installed **on Windows** and connects to Ubuntu through the WSL extension.

## Step 1: Install VS Code on Windows

Download the Windows installer from [code.visualstudio.com](https://code.visualstudio.com/) and run it. Keep the default options; in particular, leave **Add to PATH** checked.

<!-- SCREENSHOT: VS Code Windows installer "Select Additional Tasks" page with "Add to PATH" checked -->

## Step 2: Install the WSL extension

In **PowerShell** (not Ubuntu):

```powershell
code --install-extension ms-vscode-remote.remote-wsl
```

This installs the extension that lets VS Code on Windows work inside Ubuntu. If `code` isn't recognized, close and reopen PowerShell; the installer added it to your `PATH`.

## Step 3: Open VS Code from Ubuntu

In the **Ubuntu** terminal:

```bash
cd ~/projects && code .
```

The first time, this installs a small VS Code server inside Ubuntu and then opens a VS Code window. If VS Code asks whether you trust the authors of the files in this folder, click **Yes, I trust the authors**.

Check the **bottom-left corner** of the VS Code window: it should say **WSL: Ubuntu**.

<!-- SCREENSHOT: VS Code window with "WSL: Ubuntu" shown in the bottom-left remote indicator -->

## Step 4: Install the course extensions

Back in the **Ubuntu** terminal, run each line:

```bash
code --install-extension ms-python.python
```

```bash
code --install-extension tamasfe.even-better-toml
```

These install the **Python** extension (running, debugging, and linting Python) and **Even Better TOML** (for Poetry's `pyproject.toml` files). Running these from Ubuntu installs them *inside WSL*, which is where your code runs.

## Step 5: Open a terminal inside VS Code

In VS Code, press **Ctrl+`** (the backtick key, above **Tab**). A terminal opens at the bottom. Its prompt should look like `your-username@…:~/projects$`, which means it's a Ubuntu terminal. You can use it for everything in this course.

:::{tip}
From now on, the usual way to work is: open Ubuntu, `cd` into a project under `~/projects`, and run `code .`.
:::

Next: [](05-gcloud.md).
