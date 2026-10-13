---
title: Before you start (Mac)
---

Read this page before you install anything. It explains the few ideas the rest of Part 2 relies on.

## Terminal and zsh

**Terminal** is the Mac app that gives you a command line. Inside it runs a **shell**, the program that reads your commands. On current Macs the shell is **zsh**. macOS is Unix-based, like Linux, so nearly every command you learn here works the same on the Linux servers you'll use later.

To open Terminal: press **Cmd+Space**, type `Terminal`, and press **Enter**.

## Homebrew

**Homebrew** is a package manager: one command installs, updates, or removes a tool. You'll install **everything** in this part with Homebrew, so updates are always the same: `brew upgrade`.

macOS includes old versions of some tools, such as Git and Python. Homebrew installs current versions alongside them, and the `PATH` setting below makes sure the Homebrew versions win.

## PATH

When you type a command like `git`, your shell searches a list of folders for a program with that name. That list is the **PATH**. Homebrew installs into its own folder:

| Mac type | Homebrew folder |
| --- | --- |
| Apple Silicon (M1 or newer) | `/opt/homebrew` |
| Intel | `/usr/local` |

On Apple Silicon you'll add `/opt/homebrew/bin` to your PATH in step 1. To check which kind of Mac you have, click the **Apple menu → About This Mac** and look at **Chip** (Apple M-something) or **Processor** (Intel).

:::{note}
Some steps change your PATH. Because a terminal reads PATH only when it starts, those steps tell you to **close and reopen Terminal**. Don't skip it.
:::

## What you'll install, in order

1. **Homebrew**, plus Apple's Command Line Tools
2. **Git and the GitHub CLI (`gh`)**
3. **Python, pipx, and Poetry**
4. **VS Code** and its extensions
5. **The Google Cloud CLI (`gcloud`)**

## What you need

- macOS with your Mac's login password (you'll need administrator rights)
- About 10 GB of free disk space
- 45–60 minutes

Ready? Start with [](01-homebrew.md).
