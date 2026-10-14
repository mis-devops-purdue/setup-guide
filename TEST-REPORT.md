# Phase 1 test report

What was tested, where, and what still needs a manual check.

## Summary

| Area | Tested where | Result |
| --- | --- | --- |
| Book builds (Jupyter Book 2.1.7, `--strict`) | Rob's Mac (isolated venv, outside Homebrew) | ✅ 24 pages, 0 errors, 0 warnings |
| Cross-references and labels | Same build (`--strict`) | ✅ All resolve |
| External links (`--check-links`) | Same build, after both repos were public | ✅ All resolve |
| GitHub Actions deploy with `BASE_URL=/setup-guide` | GitHub Actions | ✅ Passed |
| Live site | `https://mis-devops-purdue.github.io/setup-guide/` | ✅ All 24 pages return 200; CSS loads from `/setup-guide/` |
| `verify.sh` ShellCheck | ShellCheck 0.11.0 locally, plus CI in `verify-setup` | ✅ No warnings |
| `verify.sh` under bash 3.2 | `/bin/bash` 3.2.57 on macOS | ✅ Runs; results correct (see below) |
| `verify.sh` student flow | `gh repo clone mis-devops-purdue/verify-setup` → `bash verify-setup/verify.sh` | ✅ Works |
| `verify.sh` with nothing installed | macOS, `PATH=/usr/bin:/bin` | ✅ Each missing tool fails cleanly with a fix hint; no shell errors |
| `verify.sh` Cloud Shell code path | macOS with `CLOUD_SHELL=true` (simulated) | ✅ Skips pipx and VS Code; flags Poetry outside `$HOME` |
| Part 2 (Mac) steps | **Not run.** Rob's tools weren't changed, and no throwaway user was used. | ⏳ Manual |
| Part 1 (WSL) Linux steps | **Not run.** Docker wasn't available. | ⏳ Manual |
| Part 3 (Cloud Shell) steps and `verify.sh` there | **Not run.** Rob declined `gcloud cloud-shell ssh` testing. | ⏳ Manual |

## `verify.sh` on Rob's Mac

12 passed, 4 failed. All four failures are real differences between Rob's machine and the guide's Mac path, so the script behaved correctly:

- `pipx` isn't installed (Rob's Poetry comes from Homebrew, not pipx)
- Poetry export plugin missing
- `virtualenvs.in-project` not set
- `tamasfe.even-better-toml` extension not installed

To see a full PASS on this Mac, follow Part 2 pages 3–4. This changes Rob's Poetry setup, so it was left for Rob to decide.

## Still needs a manual check

1. **Windows side of Part 1**, on a real Windows machine: `wsl --install`, the restart, Linux user creation, `wsl -l -v`, the VS Code installer, and `code --install-extension ms-vscode-remote.remote-wsl` from PowerShell.
2. **WSL Linux steps** in a fresh Ubuntu (current WSL default): apt updates, the `gh` apt repo, `pipx` from apt, Poetry and the export plugin, the gcloud apt repo, `gcloud auth login` (browser and `localhost` behavior).
3. **`verify.sh` on WSL.** These paths weren't exercised:
   - WSL detection from `/proc/version`
   - the `/mnt/c` warning
   - the `~/.vscode-server` guard
   - `code --list-extensions` run from inside WSL. The script assumes this lists the WSL-side extensions, and that working at all implies the WSL extension is installed. Please confirm.
4. **`verify.sh` in Git Bash on Windows**, to confirm the "outside WSL" ❌ message.
5. **Part 2 on a clean Mac** (or a throwaway user): Homebrew's install and PATH steps on Apple Silicon and Intel, `brew install --cask gcloud-cli` putting `gcloud` on PATH, and `code` on PATH after the VS Code cask.
6. **Part 3 in a fresh Cloud Shell**:
   - whether `gh` is preinstalled; if not, the `~/.local/bin` install
   - the `~/.bashrc` PATH line
   - Poetry's official installer and `poetry self add poetry-plugin-export`
   - whether the Python extension appears in the Editor's Installed list
   - the real `verify.sh` run
7. **Screenshots**: all 17 placeholders in `SCREENSHOTS.md`.
8. **Placeholder**: `{{GCP_ACCOUNT_INSTRUCTIONS_URL}}` appears as literal text on the live site until replaced (see README).

## Uninstall section

Added after Troubleshooting: `uninstall/` (4 pages).

| Area | Tested where | Result |
| --- | --- | --- |
| Pages build and cross-references | Strict build with `--check-links` (28 pages) | ✅ 0 errors, 0 warnings |
| Command syntax | Every `bash` block parsed with `bash -n` (41 blocks) | ✅ No syntax errors |
| Running the commands | **Not run anywhere.** They would remove tools from Rob's Mac. | ⏳ Manual |

Commands come from official docs where docs exist:
- **Cloud Shell reset:** Google's "Resetting Cloud Shell" page (`sudo rm -rf $HOME`, then **More → Restart**).
- **Homebrew uninstaller:** Homebrew's install repo.
- **`wsl --unregister`:** Microsoft's WSL basic-commands page.
- **gcloud:** Google's uninstall page says only to use the OS package manager for apt installs. The apt source and key paths in the guide mirror the setup steps.

Still needs a manual check:
- **Option A on a WSL machine and on a Mac**, ideally right after a fresh setup, then confirm `verify.sh` reports the tools as missing.
- **The Windows Settings route for uninstalling WSL** (B2). It isn't covered by Microsoft's command docs.
- **Cloud Shell reset**: confirm the **More → Restart** menu wording, and that the home folder is back to defaults.

## Notes

- GitHub's `ubuntu-latest` runners move to Ubuntu 26 starting October 19, 2026. The deploy workflow only needs Node, so this shouldn't matter. The guide doesn't name an Ubuntu version; it requires Python 3.11+, which every current Ubuntu LTS meets.
- Versions current at testing: Poetry 2.5.x, `gh` 2.102, Homebrew cask `gcloud-cli` (formerly `google-cloud-sdk`), Cloud Shell Python 3.12 per Google's docs.
