# Agent Build & Test Instructions

This repository is a Hugo site that uses the Adritian Free Hugo Theme as a Hugo module.

## Prerequisites

- Hugo **Extended** `>= 0.153.0`
- Go `>= 1.23`
- Node.js `>= 20`

## Build setup

1. Download/update the theme module:

   ```bash
   hugo mod get -u github.com/zetxek/adritian-free-hugo-theme
   ```

2. Generate npm package metadata from Hugo modules:

   ```bash
   hugo mod npm pack
   ```

3. Install Node dependencies:

   ```bash
   npm install
   ```

## Run locally

```bash
hugo server -D
```

## Build for production

```bash
hugo --minify
```

## Test / verification checks

Run these checks before opening a PR:

```bash
# Validate templates/content can render
hugo --printPathWarnings --panicOnWarning

# Verify module graph resolves correctly
hugo mod graph
```

If either command fails due to missing tools, install prerequisites first and re-run.


## Troubleshooting: `hugo: command not found`

Common causes in CI/agent containers:

- Base image does not include Hugo.
- Network restrictions block install endpoints (e.g. Go proxy, Snap store, package mirrors).

Recommended fixes:

1. **Preinstall Hugo Extended in the base image** used by the environment.
2. **Pin Hugo setup in CI** (for GitHub Actions, use `peaceiris/actions-hugo@v3` with `extended: true`).
3. Keep a version check in the pipeline:

```bash
hugo version  # output must include `extended`
```
