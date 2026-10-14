---
title: Troubleshooting
---

Find your problem below. If nothing here fixes it, contact the instructor or TA with your part (Windows, Mac, or Cloud Shell), the step, the command, and the full error message.

## All platforms

(command-not-found)=
### `command not found` right after installing something

Your terminal reads `PATH` (the list of folders it searches for commands) only when it starts.

1. **Close the terminal window completely and open a new one.** This fixes most cases.
2. Still not found? Check what's on your PATH:

   ```bash
   echo "$PATH" | tr ':' '\n'
   ```

   - For tools installed with pipx or the Poetry installer, `~/.local/bin` (shown as `/home/you/.local/bin` or `/Users/you/.local/bin`) should be listed. If it isn't, run `pipx ensurepath` (Windows/Mac) or repeat [step 5 of Cloud Shell page 1](#cloud-shell-path) and reopen the terminal.
   - On an Apple Silicon Mac, `/opt/homebrew/bin` should be listed. If it isn't, repeat [Mac page 1, step 3](#mac-homebrew-path).

### Git asks for a username and password

Passwords don't work with GitHub when two-factor authentication is on. Make sure `gh` is signed in and that Git uses it:

```bash
gh auth status
```

```bash
gh auth setup-git
```

The second command tells Git to get your GitHub credentials from `gh`.

### `gh auth status` says the token is invalid

Sign in again:

```bash
gh auth login --hostname github.com --git-protocol https --web
```

(python-too-old)=
### Python is older than 3.11

- **Mac:** run `brew install python`, then close and reopen Terminal. `which python3` should point to `/opt/homebrew/bin/python3` (Apple Silicon) or `/usr/local/bin/python3` (Intel), not `/usr/bin/python3`.
- **Windows (WSL):** your Ubuntu is an old release. In PowerShell, run `wsl -l -v` to see it, and contact the instructor or TA before changing anything. Upgrading Ubuntu is possible but takes care.
- **Cloud Shell:** this shouldn't happen. Contact the instructor or TA.

### `poetry export` says the command doesn't exist

The export plugin isn't installed in the same place as Poetry.

- **Windows/Mac (pipx):** `pipx inject poetry poetry-plugin-export`
- **Cloud Shell (official installer):** `poetry self add poetry-plugin-export`

## Windows (WSL)

(wsl-virtualization)=
### Error 0x80370102, or a message about virtualization

WSL 2 needs your processor's **virtualization** feature, which is sometimes turned off in the computer's firmware (BIOS/UEFI).

1. Open **Task Manager** (Ctrl+Shift+Esc) → **Performance** → **CPU**. Look for **Virtualization: Enabled**.
2. If it says **Disabled**, restart into your computer's BIOS/UEFI settings (the key varies by manufacturer: often F2, F10, F12, or Del during startup) and enable **Intel VT-x**, **Intel Virtualization Technology**, or **AMD-V / SVM Mode**. Save and restart.
3. In PowerShell as administrator, make sure the Windows feature is on, then restart:

   ```powershell
   wsl --install --no-distribution
   ```

If your computer is managed by an employer and you can't change these settings, use [Part 3: Cloud Shell](cloud-shell/before-you-start.md).

### `wsl --install` prints help text instead of installing

WSL is already partly installed. Install Ubuntu by name:

```powershell
wsl --install -d Ubuntu
```

### The install is stuck at 0.0%

Press **Ctrl+C** and download it a different way:

```powershell
wsl --install --web-download -d Ubuntu
```

### My files are under `/mnt/c`

Projects should live in your Linux home folder. Move a project into it (replace the path with yours):

```bash
mv /mnt/c/Users/YourWindowsName/path/to/project ~/projects/
```

Then work from `~/projects/project`. See [](windows/before-you-start.md) for why.

### `code .` in Ubuntu doesn't open VS Code

1. Make sure VS Code is installed on **Windows** and the WSL extension is installed ([Windows page 4](windows/04-vs-code.md)).
2. Close and reopen the Ubuntu terminal.
3. In PowerShell, run `wsl --shutdown`, then open Ubuntu again.

### `gcloud auth login` can't reach `localhost`

Press **Ctrl+C** and use the copy-and-paste flow instead:

```bash
gcloud auth login --no-launch-browser
```

### I forgot my Linux password

In PowerShell, open Ubuntu as the root user and set a new password (replace `your-username`):

```powershell
wsl -u root
```

```bash
passwd your-username
```

Type `exit` to leave.

## Mac

### `xcrun: error: invalid active developer path`

Apple's Command Line Tools are missing, often after a macOS update. Reinstall them:

```bash
xcode-select --install
```

### `brew: command not found` on an Apple Silicon Mac

Homebrew isn't on your PATH. Repeat [Mac page 1, step 3](#mac-homebrew-path), then close and reopen Terminal.

### `which code` prints nothing

Open VS Code, press **Cmd+Shift+P**, choose **Shell Command: Install 'code' command in PATH**, then close and reopen Terminal.

## Cloud Shell

### A tool I installed is gone after reconnecting

It was installed outside your home folder, which is erased at the end of every session. Reinstall it the Part 3 way, under `~/.local/bin`.

### Poetry stopped working after Cloud Shell was updated

Google occasionally updates Cloud Shell's Python, which can break a Poetry installed against the old version. Reinstall it:

```bash
curl -sSL https://install.python-poetry.org | python3 - --uninstall
```

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

```bash
poetry self add poetry-plugin-export
```

Your `virtualenvs.in-project` setting is kept.

### Cloud Shell says I've used my weekly quota

The weekly quota is 50 hours by default. Until it resets, work locally if you can, and contact the instructor or TA if a deadline is at risk.

### My session keeps disconnecting

Cloud Shell ends sessions after about an hour without activity. Click **Reconnect**. Your home folder is kept.
