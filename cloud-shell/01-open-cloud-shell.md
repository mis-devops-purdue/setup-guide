---
title: 1. Open Cloud Shell
---

## Step 1: Open Cloud Shell

Go to **[shell.cloud.google.com](https://shell.cloud.google.com/)** and sign in with your course Google account.

- If you're asked to accept the Google Cloud **Terms of Service**, accept them.
- If you're offered a **free trial** or asked for a **credit card**, close that page. You don't need it.

After a moment you'll see the **Cloud Shell Editor** on top and a **terminal** underneath.

<!-- SCREENSHOT: Cloud Shell in the browser with the Editor above and the terminal below -->

:::{tip}
Bookmark `https://shell.cloud.google.com/`. It's how you'll get back here every time.
:::

## Step 2: Learn the toolbar buttons

At the top of the terminal panel:

- **Open Editor / Open Terminal** switches between showing the Editor and showing only the terminal.
- **Web Preview** (an eye-shaped or window icon) opens an app you're running in Cloud Shell in a new browser tab. You'll use it later in the course when you run a web app; you don't need it today.
- **+** opens another terminal tab.

<!-- SCREENSHOT: Cloud Shell toolbar with the Open Editor and Web Preview buttons labeled -->

## Step 3: Check where you are

```bash
cd ~ && pwd
```

This moves to your home folder and prints its path, such as `/home/your_name`. Remember: **only this folder is kept between sessions.**

## Step 4: Create your projects folder

```bash
mkdir -p ~/projects
```

This creates a `projects` folder in your home folder for your course work.

(cloud-shell-path)=
## Step 5: Add `~/.local/bin` to your PATH

You'll install tools into `~/.local/bin`, inside your home folder, so they survive restarts. Make sure the terminal always looks there:

```bash
grep -q 'HOME/.local/bin' ~/.bashrc || echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
```

This adds one line to `~/.bashrc` (a settings file that runs whenever a terminal starts) unless it's already there.

```bash
source ~/.bashrc
```

This applies the change to the terminal you have open now.

Next: [](02-git-and-github.md).
