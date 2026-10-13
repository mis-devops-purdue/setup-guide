:::{dropdown} Sidebar: How SSH keys work (optional reading, no steps required)
You'll see some tutorials connect to GitHub with **SSH keys** instead of HTTPS. We use HTTPS with `gh` because it's one command and works everywhere, but the SSH idea is worth knowing, because servers use it constantly.

- An SSH **key pair** is two files. The **private key** stays on your computer and is never shared. The **public key** can be given to anyone.
- You upload your **public** key to GitHub (or to a server).
- When you connect, the server sends a challenge that only your **private** key can answer. If the answer checks out against the public key, you're in. No password ever crosses the network.
- That's also why you never copy a private key into a chat, an email, or a repository: anyone holding it *is* you.

You **don't** need to create an SSH key for this course.
:::
