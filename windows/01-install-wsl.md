---
title: 1. Install WSL and Ubuntu
---

## Step 1: Open PowerShell as administrator

Click **Start**, type `PowerShell`, right-click **Windows PowerShell**, and choose **Run as administrator**. Click **Yes** when Windows asks for permission.

<!-- SCREENSHOT: Start menu with "Run as administrator" highlighted for Windows PowerShell -->

## Step 2: Install WSL

```powershell
wsl --install
```

This turns on the Windows features WSL needs and downloads Ubuntu. It takes a few minutes.

:::{note}
If this prints a list of help text instead of installing, WSL is already partly installed. Run `wsl --install -d Ubuntu` instead. If the download sits at 0.0% for several minutes, press **Ctrl+C** and run `wsl --install --web-download -d Ubuntu`.
:::

## Step 3: Restart your computer

Restart when the install finishes. This is required.

## Step 4: Create your Linux username and password

After the restart, an **Ubuntu** window opens by itself. (If it doesn't, click **Start**, type `Ubuntu`, and open it.) Wait for it to finish installing, then:

1. Enter a **username**: lowercase, no spaces (for example `jsmith`). It doesn't have to match your Windows name.
2. Enter a **password**, then enter it again.

<!-- SCREENSHOT: Ubuntu first-run window asking for a new UNIX username -->

:::{important} Remember this password
Nothing appears on screen while you type a password in Linux. That's normal; keep typing and press **Enter**. You'll need this password every time a command starts with `sudo` (run as administrator). Write it down somewhere safe.
:::

If you see an error such as **0x80370102** or a message about **virtualization**, see [](#wsl-virtualization).

## Step 5: Update Ubuntu

In the Ubuntu window:

```bash
sudo apt update && sudo apt upgrade -y
```

This downloads the latest package lists and installs updates. Enter your Linux password when asked.

## Step 6: Confirm you're on WSL 2

Back in **PowerShell** (it doesn't need to be administrator this time):

```powershell
wsl -l -v
```

You should see **Ubuntu** with **VERSION 2**. If it shows 1, run `wsl --set-version Ubuntu 2`.

## Step 7: Create your projects folder

From here on, every command goes into the **Ubuntu** terminal unless the step says otherwise.

```bash
mkdir -p ~/projects && cd ~/projects && pwd
```

This creates a `projects` folder in your Linux home and moves into it. `pwd` should print `/home/your-username/projects`, **not** something starting with `/mnt/c`.

:::{tip} Use Windows Terminal
**Windows Terminal** (preinstalled on Windows 11, free in the Microsoft Store on Windows 10) can open Ubuntu in tabs. Click the **⌄** next to the tab bar and choose **Ubuntu**.
:::

Next: [](02-git-and-github.md).
