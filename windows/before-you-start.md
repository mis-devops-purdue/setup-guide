---
title: Before you start (Windows)
---

Read this page before you install anything. It explains what you're about to set up and why.

## What is WSL?

**WSL (Windows Subsystem for Linux)** runs a real Linux system inside Windows. It isn't an emulator, and you don't need to restart to switch between them. You'll install **Ubuntu**, the most popular Linux distribution, and use it as your command line for the whole course.

After setup you'll have two worlds on one laptop:

| | Windows | Ubuntu (inside WSL) |
| --- | --- | --- |
| Terminal | PowerShell | **Ubuntu** terminal (bash) |
| Your home folder | `C:\Users\you` | `/home/you`, written `~` |
| Install software with | installers, Microsoft Store | `sudo apt install …` |
| What runs here in this course | VS Code's window, your web browser | Git, `gh`, Python, Poetry, `gcloud`, your code |

## Two file systems, and why your work lives in `~/`

Ubuntu has its own Linux file system. It can also see your Windows drive at `/mnt/c`, but **don't keep course projects there**:

- **Speed.** Tools working on files under `/mnt/c` cross between Windows and Linux on every file read, which is many times slower.
- **Compatibility.** File permissions and line endings work differently on the Windows side, which breaks scripts in confusing ways.
- **Reliability.** Tools that watch for file changes (such as auto-reloading web servers) often miss changes under `/mnt/c`.

**Rule for this course:** keep everything under your Linux home folder, `~/`. You'll create `~/projects` for this.

:::{tip} Finding your Linux files from Windows
In File Explorer, click **Linux → Ubuntu → home → *your-username*** in the left sidebar. You can open and copy files there, but do your work through the Ubuntu terminal and VS Code.
:::

## How VS Code fits in

You'll install VS Code **on Windows**. The **WSL extension** then connects it to Ubuntu: the window is on Windows, but your files, terminal, and Python all run inside Linux. That gives you a normal Windows app and a real Linux environment together.

## What you'll install, in order

1. **WSL and Ubuntu**: the Linux system itself
2. **Git and the GitHub CLI (`gh`)**: version control and GitHub sign-in
3. **Python, pipx, and Poetry**: Python and the tool that manages project dependencies
4. **VS Code** and its extensions: your editor
5. **The Google Cloud CLI (`gcloud`)**: the command-line tool for Google Cloud

## What you need

- Windows 10 version 2004 or later, or Windows 11. To check, press **Windows key + R**, type `winver`, and press **Enter**.
- Administrator rights on your computer
- About 10 GB of free disk space
- 60–90 minutes, including one restart

Ready? Start with [](01-install-wsl.md).
