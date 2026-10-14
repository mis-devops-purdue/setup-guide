# MIS 58710 Setup Guide

The student-facing setup guide for **MIS 58710 DevOps and Technology Solutions**, built with [Jupyter Book 2](https://jupyterbook.org) (MyST engine) and published at:

**https://mis-devops-purdue.github.io/setup-guide/**

Students complete it in Week 1 as **Prep 2 – Setup**. The guide is reusable across semesters, so keep dates, semester names, and section-specific details out of it; refer to sessions only as `Week.Session` (for example, "ICE 2 at 2.1").

## Structure

| Path | What it is |
| --- | --- |
| `myst.yml` | Project config and the explicit table of contents |
| `index.md`, `why-linux.md`, `choose-your-path.md` | Front matter |
| `windows/`, `mac/`, `cloud-shell/` | Parts 1–3. Each opens with `before-you-start.md`, then numbered step pages. |
| `verify.md` | Runs [`verify-setup`](https://github.com/mis-devops-purdue/verify-setup); the last page before STOP HERE |
| `stop-here.md` | End of Week 1 setup |
| `troubleshooting.md` | Common problems, with MyST labels the other pages link to |
| `uninstall/` | "Undo your setup": a shared page (save work, sign out), Windows and Mac pages (A: course tools only, B: everything), and a Cloud Shell reset page |
| `_parts/sidebar-footer.md` | Replaces "Made with MyST" at the bottom of the sidebar. The navbar text is set by `site.options.logo_text` in `myst.yml`. |
| `_snippets/` | Text shared by all three parts (Git config, `gh auth login`, SSH sidebar, Poetry config, and so on), pulled in with `{include}`. Excluded from the TOC. |
| `SCREENSHOTS.md` | Every screenshot placeholder, with page and line |
| `.github/workflows/deploy.yml` | Builds the book and deploys it to GitHub Pages |

## Placeholders to fill in

These instructor-specific values appear as literal `{{NAME}}` text in the pages. Replace them before each semester (search the repo for `{{`).

| Placeholder | Used in | Replace with |
| --- | --- | --- |
| `{{GCP_ACCOUNT_INSTRUCTIONS_URL}}` | `windows/05-gcloud.md`, `mac/05-gcloud.md`, `cloud-shell/before-you-start.md` | A link to instructions on which Google account students should use for Google Cloud |

Screenshot placeholders are HTML comments (`<!-- SCREENSHOT: … -->`) and are listed in [`SCREENSHOTS.md`](SCREENSHOTS.md).

## Build locally

Jupyter Book 2 needs Python and Node.js 20 or newer.

```bash
pipx install "jupyter-book>=2"     # or: pip install "jupyter-book>=2" in a virtual environment
jupyter book start                 # live preview at http://localhost:3000
```

To check exactly what CI builds:

```bash
BASE_URL=/setup-guide jupyter book build --html --strict
```

Add `--check-links` to also check every external link.

## Deploy

Every push to `main` runs `.github/workflows/deploy.yml`, which builds the site with `BASE_URL=/setup-guide` and deploys it to GitHub Pages. Under **Settings → Pages**, **Source** must be set to **GitHub Actions**.

`BASE_URL` must match the repository name. If the repo is renamed, update it in the workflow, or the site's styling breaks.

## Later chapters (Phase 2)

The `later/` chapters (Claude Code, GCP project and BigQuery, GitLab, Postman/Bruno) aren't written yet. They'll be added to the TOC **after** `stop-here.md` so that nothing before STOP HERE covers them. When they're added, the uninstall pages need matching removal steps.
