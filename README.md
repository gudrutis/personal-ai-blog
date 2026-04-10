# Personal Blog + Portfolio (Hugo MVP)

A Hugo starter for a personal blog + portfolio with Bootstrap and custom styling.

## Quick start

1. Install Hugo Extended.
2. Run locally:

```bash
hugo server -D
```

3. Create a new post:

```bash
hugo new blog/my-new-post.md
```

4. Mark a post as ready by changing front matter:

```toml
draft = false
```

## Deploy to GitHub Pages (step-by-step)

### 1) Push this repo to GitHub

```bash
git remote add origin https://github.com/<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

### 2) Enable GitHub Pages to deploy from Actions

In your GitHub repo:

- Go to **Settings → Pages**.
- Under **Build and deployment**, set **Source = GitHub Actions**.

### 3) Make sure Actions have permission

In **Settings → Actions → General → Workflow permissions**, choose:

- **Read and write permissions**
- Enable **Allow GitHub Actions to create and approve pull requests** (optional)

### 4) Set your site URL in `hugo.toml`

Update `baseURL`:

```toml
baseURL = 'https://<your-username>.github.io/<repo-name>/'
```

### 5) Publish when content is ready (tag release)

This project deploys only when you push a version tag matching `v*`.

```bash
git add .
git commit -m "Publish site updates"
git push origin main

git tag v0.1.0
git push origin v0.1.0
```

### 6) Check deployment status

- Open the **Actions** tab and wait for workflow `Deploy Hugo site to GitHub Pages`.
- Once complete, your site will be live at:
  - `https://<your-username>.github.io/<repo-name>/`


## Go live from GitHub (quick path)

1. Create a GitHub repo and push this project:

```bash
git remote add origin https://github.com/<your-username>/<repo-name>.git
git branch -M main
git push -u origin main
```

2. In GitHub repo settings, enable Pages from Actions:
   - **Settings → Pages → Source: GitHub Actions**

3. Update `hugo.toml` `baseURL` to:

```toml
baseURL = 'https://<your-username>.github.io/<repo-name>/'
```

4. Publish site when ready by pushing a version tag (`v*`):

```bash
git add .
git commit -m "Publish updates"
git push origin main
git tag v0.1.0
git push origin v0.1.0
```

5. Watch **Actions** tab until workflow succeeds, then open:
   - `https://<your-username>.github.io/<repo-name>/`

## Add images from VS Code

- Put files in `static/images/`.
- Refer to them in Markdown as:

```md
![Screenshot](/images/example.png)
```

## Future improvements

- Add a shop link to menu in `hugo.toml`.
- Add analytics (Plausible/Google Analytics) in `layouts/partials/head.html`.
- Add comments/search integration.
