---
title: Uninstall on Mac
---

Do [](index.md) first: save your work and sign out.

Choose **one** option:

- **Option A: remove the course tools only.** Keeps Homebrew, Git, and Python, which other software on your Mac may use.
- **Option B: remove everything.** Also removes Homebrew and everything installed with it. Use this only if you didn't use Homebrew before this course.

:::{warning} Did you use these tools before the course?
If Homebrew, Git, or Python were already on your Mac before you started this guide, other software may depend on them. Use Option A, and skip any step that removes a tool you were already using.
:::

## Option A: Remove the course tools only

Run these commands in **Terminal**. They undo the setup in reverse order.

### A1: Remove the Google Cloud CLI

```bash
brew uninstall --cask gcloud-cli
```

Remove your `gcloud` settings:

```bash
rm -rf ~/.config/gcloud
```

### A2: Remove the VS Code extensions

```bash
code --uninstall-extension ms-python.python
```

```bash
code --uninstall-extension tamasfe.even-better-toml
```

### A3: Remove VS Code

```bash
brew uninstall --cask visual-studio-code
```

To also remove VS Code's settings and extensions:

```bash
rm -rf ~/Library/Application\ Support/Code ~/.vscode
```

### A4: Remove Poetry and pipx

```bash
pipx uninstall poetry
```

This removes Poetry and its export plugin together.

Remove Poetry's settings and download cache:

```bash
rm -rf ~/Library/Application\ Support/pypoetry ~/Library/Caches/pypoetry
```

Remove pipx:

```bash
brew uninstall pipx
```

`pipx ensurepath` added a line to your shell's startup file (usually `~/.zshrc`) that puts `~/.local/bin` on your PATH. It's harmless to leave.

### A5: Remove the GitHub CLI

```bash
brew uninstall gh
```

Remove `gh`'s settings:

```bash
rm -rf ~/.config/gh
```

### A6: Remove your Git settings

```bash
git config --global --unset user.name
```

```bash
git config --global --unset user.email
```

```bash
git config --global --unset init.defaultBranch
```

### A7: Clean up Homebrew

```bash
brew autoremove && brew cleanup
```

This removes packages that were only installed to support the tools above, and deletes old downloads.

Git and Python stay installed. They're useful beyond this course, and other tools often need them. To remove them anyway, run `brew uninstall git python`. Homebrew refuses if something else still depends on them.

(uninstall-mac-files)=
### A8: Remove the course files (optional)

:::{danger} This deletes your course work
Only run this after you've pushed everything you want to keep (see [](index.md)).
:::

```bash
rm -rf ~/projects ~/verify-setup
```

## Option B: Remove everything

### B1: Remove the course tools

Do **Option A, steps A1 to A6** above. This removes each tool's settings, which uninstalling Homebrew doesn't do.

### B2: Uninstall Homebrew

:::{danger} This removes every Homebrew package
Everything installed with `brew`, including tools you installed for other reasons, is removed.
:::

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"
```

This runs Homebrew's official uninstaller. It lists what it will remove and asks you to confirm. It may also ask for your Mac password. When it finishes, it may list leftover folders it couldn't remove; you can delete them with the commands it prints.

Then remove the PATH line you added during setup. Open `~/.zprofile`:

```bash
open -e ~/.zprofile
```

Delete the line containing `brew shellenv`, save, and close the file.

### B3: Remove the course files (optional)

Same as [step A8](#uninstall-mac-files).

Apple's Command Line Tools stay installed. macOS and many other apps use them, so leave them in place.
