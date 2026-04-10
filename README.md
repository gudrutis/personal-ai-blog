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

## Publishing strategy

This repo deploys to GitHub Pages when you push a Git tag that starts with `v`.

Example:

```bash
git tag v0.1.0
git push origin v0.1.0
```

Use this as your “ready to publish” checkpoint.

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
