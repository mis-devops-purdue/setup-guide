---
title: 3. Python and Poetry
---

All commands on this page go into the **Ubuntu** terminal.

**Poetry** manages a Python project's dependencies and virtual environment. You'll install it with **pipx**, a tool that installs Python command-line apps into their own isolated environments so they can't break each other (or Ubuntu's own Python).

## Step 1: Check Python

Ubuntu includes Python 3:

```bash
python3 --version
```

You need **3.11 or newer**. Current Ubuntu releases include a recent enough version. If yours is older, see [](#python-too-old).

## Step 2: Install pipx

```bash
sudo apt install -y pipx
```

This installs pipx from Ubuntu's packages.

## Step 3: Add pipx's folder to your PATH

```bash
pipx ensurepath
```

This adds `~/.local/bin`, where pipx puts the apps it installs, to your `PATH`.

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
