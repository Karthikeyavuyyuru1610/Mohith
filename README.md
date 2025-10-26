# Simple Chatbot (Static Web Project)

This is a small static web project containing a frontend chatbot UI. It can be hosted on GitHub Pages as a static site.

## Project structure

- `index.html` — entry page
- `css/` — styles
  - `style.css`
- `js/` — JavaScript
  - `main.js`

(If your project contains additional files, list them here.)

## Quick local preview

Open `index.html` in your browser, or run a simple local static server. Using PowerShell, you can run:

```powershell
# if you have Python 3 installed
python -m http.server 8000
# then open http://localhost:8000 in your browser
```

Or with Node.js installed, a one-liner if you have `http-server`:

```powershell
npx http-server -p 8000
```

## How to push this project to GitHub (PowerShell)

1. Create a repository on GitHub (via the website). Note the repository URL (e.g., `https://github.com/your-username/your-repo.git`).

2. From the project root (`c:\Users\karth\Desktop\chatbot\New folder`), run these commands in PowerShell:

```powershell
# initialize git (if not already a git repo)
git init
# add files
git add .
# commit
git commit -m "Initial commit"
# set main branch name
git branch -M main
# add remote (replace URL with your repo URL)
git remote add origin https://github.com/your-username/your-repo.git
# push to GitHub
git push -u origin main
```

If you use SSH remote URLs, replace the `https://...` URL above with the SSH URL.

Note: You will be prompted for credentials or a token when pushing over HTTPS unless you have a credential helper set up.

## Enable GitHub Pages

There are two common, easy ways to publish:

Option A — Use the `main` branch root
- On GitHub, open your repository.
- Go to Settings -> Pages.
- Under "Source", choose: Branch `main` and folder `/ (root)`.
- Save. GitHub will publish your site at `https://your-username.github.io/your-repo/` within a minute or two.

Option B — Use `gh-pages` branch (deploy branch)
- You can create a `gh-pages` branch and push build output there, or use a deployment action to publish.

## Optional: Automatic deployment with GitHub Actions

If you'd like every push to `main` to be published automatically, create a workflow at `.github/workflows/gh-pages.yml` with something like this (paste this into that file):

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./
```

This workflow checks out the repo and deploys the repository root (all static files) to the `gh-pages` branch which GitHub Pages can serve. After adding this, push it to `main` and GitHub Actions will run.

If you prefer to publish from the `main` branch root (Option A above), you don't need the workflow.

## What I can't do from here

I cannot push to your GitHub repository or enable the Pages setting for you because that requires your GitHub credentials and access to your account. Follow the exact commands above in PowerShell to push and enable Pages.

If you'd like, I can generate the `.github/workflows/gh-pages.yml` file for you here so you can just commit and push it — tell me if you want me to add it.

## Troubleshooting

- 403/401 on push: configure a personal access token (PAT) or SSH keys and add them to your GitHub account.
- Page not found after enabling: allow a minute or two for GitHub to publish, and verify the selected branch/folder.
- Asset 404s: check that paths in `index.html` to `css/` and `js/` are relative and correct.

## License

Add a license file if you want (e.g., `LICENSE` or `LICENSE.md`).

## Next steps (suggested)

- Create a GitHub repo and push using the commands above.
- Optionally add the GitHub Actions workflow file for automated deployment.
- Optionally add a `CNAME` file if you plan to use a custom domain.

---

If you want, I can now:
- create the workflow file `.github/workflows/gh-pages.yml` in your project,
- or create and commit everything and show the exact PowerShell commands to push — tell me which you'd like next.
