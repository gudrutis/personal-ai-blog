# Personal Blog + Portfolio (Hugo + Adritian Theme)

This project now uses the **Adritian Free Hugo Theme**:
https://themes.gohugo.io/themes/adritian-free-hugo-theme/

## Requirements

- Hugo Extended `>= 0.153.0`
- Go `>= 1.23`
- Node.js `>= 20` (used for theme dependencies)

## Local setup

1. Install dependencies and theme module:

```bash
hugo mod get -u github.com/zetxek/adritian-free-hugo-theme
hugo mod npm pack
npm install
```

2. Run locally:

```bash
hugo server -D
```

3. Create a post:

```bash
hugo new blog/my-new-post.md
```

## Go live from GitHub Pages

1. Push repository:

```bash
git remote add origin https://github.com/<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

2. Enable Pages deployment from Actions:
   - **Settings → Pages → Source: GitHub Actions**

3. Ensure workflow permissions:
   - **Settings → Actions → General → Workflow permissions → Read and write permissions**

4. Set `baseURL` in `hugo.toml`:

```toml
baseURL = 'https://<your-username>.github.io/<repo-name>/'
```

5. Publish updates:

```bash
git add .
git commit -m "Publish updates"
git push origin main
```

6. Verify deployment in **Actions** tab, then open:
   - `https://<your-username>.github.io/<repo-name>/`

## Notes

- Deployment runs on pushes to `main` (plus manual `workflow_dispatch`).
- Tag-trigger deploy was removed because `github-pages` environment protection can block tag-based runs.
- Theme-level customization should be done primarily via `hugo.toml`, `content/`, and `assets/css/custom.css`.
