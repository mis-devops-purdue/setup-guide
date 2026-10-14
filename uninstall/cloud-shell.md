---
title: Reset Cloud Shell
---

Cloud Shell keeps only your home folder (`$HOME`) between sessions; everything else is rebuilt each time. So to undo the course setup, delete your home folder and restart. Cloud Shell then looks exactly as it did the first time you opened it.

Do [](index.md) first: save your work and sign out of GitHub. You don't need to sign out of Google Cloud here. Cloud Shell signs you in with the Google account you used to open it.

:::{danger} This permanently deletes every file in your Cloud Shell home folder
That includes `~/projects`, your settings, and everything you installed. It can't be undone. Make sure your work is pushed to GitHub first.
:::

## Step 1: Check what you're about to delete

```bash
ls -a $HOME
```

This lists everything in your home folder, including hidden files (names starting with `.`). If anything here isn't on GitHub and you want to keep it, download it first: right-click the file in the Cloud Shell Editor's Explorer and choose **Download**.

## Step 2: Delete your home folder

```bash
sudo rm -rf $HOME
```

This deletes the contents of your home folder. You may see errors about files that can't be removed; that's expected.

## Step 3: Restart Cloud Shell

In the Cloud Shell toolbar, click **More** (**⋮**), then click **Restart**. If a confirmation dialog appears, click **Restart** again.

<!-- SCREENSHOT: Cloud Shell toolbar "More" menu with Restart highlighted -->

Cloud Shell starts a fresh machine with a new, empty home folder.

## Step 4: Check that it worked

```bash
ls -a $HOME
```

You should see only a few default files, such as `.bashrc`. Check that the course tools you installed are gone:

```bash
command -v poetry || echo "poetry removed"
```

:::{note}
If you simply stop using Cloud Shell, Google deletes your home folder automatically after 120 days without access (after an email warning). Resetting does the same thing right away.
:::
