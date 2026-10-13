---
title: 3. Python and Poetry
---

## Step 1: Check Python

Python 3 is preinstalled:

```bash
python3 --version
```

You need **3.11 or newer**. Cloud Shell comes with a recent enough version.

## Step 2: Install Poetry with the official installer

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

This downloads Poetry's official installer and runs it with Python. It puts Poetry in `~/.local/bin` and its files in `~/.local/share/pypoetry`.

:::{note} Why not pipx here?
On Windows and Mac, Part 1 and Part 2 install Poetry with pipx. In Cloud Shell, pipx isn't preinstalled and would itself have to be installed with `sudo`, which is erased at the end of each session. The official installer puts everything in your home folder, so it survives.
:::

Check it:

```bash
poetry --version
```

You should see **Poetry (version 2.x)**. If you get `command not found`, run `source ~/.bashrc` and try again.

## Step 3: Configure Poetry

```{include} ../_snippets/poetry-config.md
```

## Step 4: Add the export plugin

```bash
poetry self add poetry-plugin-export
```

This adds the `poetry export` command to Poetry. In ICE 5 you'll use it to generate a `requirements.txt` file, which Google Cloud Run needs to build your app.

Check it:

```bash
poetry export --help
```

You should see the help text for `export`, not an error saying the command doesn't exist.

Next: [](04-editor.md).
