---
title: STOP HERE
---

:::{important} Week 1 setup is done
If the verification script shows **0 failed** and you've submitted your screenshot to **Prep 2 – Setup**, you're finished with this guide for now.
:::

You now have a working Linux command line, Git and GitHub, Python and Poetry, an editor, and the Google Cloud CLI. That's everything the course needs for its first weeks.

**Don't install anything else yet.** Later chapters of this guide are opened when the course needs them, each with its own Prep assignment and due date in Brightspace. Installing tools early often means installing the wrong version or configuring it differently from the rest of the class.

If something stops working later in the semester, run the verification script again:

```bash
cd ~ && git -C verify-setup pull && bash verify-setup/verify.sh
```

It tells you exactly what's wrong and which page to revisit. [](troubleshooting.md) covers the most common problems.
