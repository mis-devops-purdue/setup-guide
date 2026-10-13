---
title: 3. Python and Poetry
---

**Poetry** manages a Python project's dependencies and virtual environment. You'll install it with **pipx**, a tool that installs Python command-line apps into their own isolated environments so they can't break each other.

## Step 1: Install Python

```bash
brew install python
```

This installs a current Python 3 from Homebrew.

```bash
python3 --version
```

You need **3.11 or newer**.

:::{note}
macOS includes an older `python3` at `/usr/bin/python3`. If `python3 --version` shows a version older than 3.11, your PATH isn't picking up Homebrew yet: close and reopen Terminal and try again.
:::

## Step 2: Install pipx

```bash
brew install pipx
```

## Step 3: Add pipx's folder to your PATH

```bash
pipx ensurepath
```

This adds `~/.local/bin`, where pipx puts the apps it installs, to your PATH.

```{include} ../_snippets/reopen-terminal.md
```

## Step 4: Install Poetry

```bash
pipx install poetry
```

Check it:

```bash
poetry --version
```

You should see **Poetry (version 2.x)**.

## Step 5: Configure Poetry

```{include} ../_snippets/poetry-config.md
```

## Step 6: Add the export plugin

```bash
pipx inject poetry poetry-plugin-export
```

This adds the `poetry export` command to Poetry. In ICE 5 you'll use it to generate a `requirements.txt` file, which Google Cloud Run needs to build your app.

Check it:

```bash
poetry export --help
```

You should see the help text for `export`, not an error saying the command doesn't exist.

Next: [](04-vs-code.md).
