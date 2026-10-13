Tell Git who you are. Git stamps this name and email on every commit you make. Use the **same email as your GitHub account** so GitHub links your commits to you. Run each line separately, replacing the text in quotes with your own details:

```bash
git config --global user.name "Your Name"
```

```bash
git config --global user.email "you@example.com"
```

Make `main` the default branch name for new repositories (it matches GitHub):

```bash
git config --global init.defaultBranch main
```

Check your settings:

```bash
git config --global --list
```

You should see `user.name`, `user.email`, and `init.defaultbranch=main`. This is one-time setup. You'll learn to *use* Git in ICE 2 at 2.1.
