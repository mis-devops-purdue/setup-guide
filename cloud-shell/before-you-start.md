---
title: Before you start (Cloud Shell)
---

Read this page before you start. Cloud Shell works differently from a laptop, and a few of its rules shape every step in Part 3.

## What Cloud Shell is

**Google Cloud Shell** is a small Linux computer that Google runs for you and that you open in a browser tab. It comes with Git, Python, and the Google Cloud CLI already installed, plus the **Cloud Shell Editor**, a browser-based editor built on the same open-source code as VS Code. You don't install anything on your own computer.

Cloud Shell is free and doesn't need a Google Cloud project or a payment method.

## Only your home folder is kept

This is the most important rule in Part 3:

- Your **home folder** (`$HOME`, also written `~`) is a **5 GB** disk that's **kept** between sessions.
- **Everything else is reset** each time a session starts. Anything installed with `sudo apt install` disappears.

So in Part 3, everything you install goes **under `$HOME`**, usually in `~/.local/bin`. That's why some steps here differ from the Windows and Mac parts.

## Sessions and limits

| Limit | What happens |
| --- | --- |
| About **1 hour** without activity | The session ends. Your home folder is kept; reconnect and carry on. |
| **12 hours** maximum per session | The session ends, even if you're active. |
| **50 hours per week** of usage | Cloud Shell is unavailable until your quota resets. |
| **120 days** without opening Cloud Shell | Google deletes your home folder (after an email warning). |

These are Google's defaults and can change; the current numbers are in Google's [Cloud Shell documentation](https://docs.cloud.google.com/shell/docs/quotas-limits).

## Why it's the fallback, not the default

Cloud Shell is a good way to get working fast, and a good backup if your laptop breaks. But:

- It isn't connected to desktop VS Code; you use the browser-based Cloud Shell Editor instead.
- The weekly quota and session timeouts can interrupt longer work.
- Some later course tools need a local install. If you start in Cloud Shell, the course will tell you when that matters.

If you can get Windows or Mac working later, switch to that part.

## What you'll set up, in order

1. **Open Cloud Shell** and the Editor
2. **Git and the GitHub CLI (`gh`)**
3. **Poetry**, installed in your home folder
4. **The Cloud Shell Editor**: a quick tour
5. **The Google Cloud CLI (`gcloud`)**: already installed; you'll just check it

## What you need

- A Google account (see {{GCP_ACCOUNT_INSTRUCTIONS_URL}} for which one to use)
- A current version of Chrome, Edge, Firefox, or Safari
- 20–30 minutes

Ready? Start with [](01-open-cloud-shell.md).
