# Personal Blog + Portfolio (Hugo + Adritian Theme)

This project now uses the **Adritian Free Hugo Theme**:
https://themes.gohugo.io/themes/adritian-free-hugo-theme/

## Requirements

- Hugo Extended `>= 0.153.0`
- Go `>= 1.23`
- Node.js `>= 20` (used for theme dependencies)

## Install Hugo (Extended)

This project requires the **extended** Hugo build.

### macOS (Homebrew)

```bash
brew install hugo
hugo version
```

### Ubuntu/Debian (Snap)

```bash
sudo snap install hugo --channel=extended
hugo version
```

### Windows (winget)

```powershell
winget install Hugo.Hugo.Extended
hugo version
```

If `hugo version` does not include `extended`, uninstall and reinstall using the commands above.


## Why Hugo may be unavailable in this environment

If you are running in a locked-down CI/container environment (like this agent runtime), `hugo` may be missing for two common reasons:

1. The image does not preinstall Hugo.
2. Network egress is restricted, so installing Hugo from package registries can fail (for example, blocked access to `proxy.golang.org`, Snap store, or Homebrew mirrors).

### Fastest way to make Hugo available

Pick one installation path below based on your environment:

- **Local machine (recommended):** install Hugo Extended with Homebrew/Snap/winget (see above).
- **Dev container / Docker image:** preinstall Hugo in the image so builds do not depend on runtime downloads.
- **GitHub Actions:** use `actions/setup-hugo` and pin an extended Hugo version.

### GitHub Actions example

```yaml
- name: Setup Hugo
  uses: peaceiris/actions-hugo@v3
  with:
    hugo-version: '0.153.0'
    extended: true

- name: Verify Hugo
  run: hugo version
```

### Verify after install

```bash
hugo version
# must include: extended

hugo --printPathWarnings --panicOnWarning
```

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
- Avoid copying full templates from other themes into `layouts/`; local layout overrides take precedence and can prevent the Adritian theme from rendering correctly.
