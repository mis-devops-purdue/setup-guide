Tell Poetry to create each project's virtual environment **inside the project folder** (as `.venv`). VS Code finds it automatically, and deleting the project removes it too:

```bash
poetry config virtualenvs.in-project true
```

Check the setting:

```bash
poetry config virtualenvs.in-project
```

It should print `true`.
