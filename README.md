# smriti-legal

Public legal pages for the Smriti reading app, hosted on GitHub Pages so the app and the Google Play Console can link to a stable, public URL.

The private `smriti` repo links to these pages; this repo is the source of truth for the legal text.

## Files

The pages live in the `docs/` folder:

- `docs/index.html`
- `docs/privacy-policy.html`
- `docs/terms.html`
- `docs/styles.css`

## GitHub Pages setup

1. Make this repo **public** — free-tier GitHub Pages requires public visibility.
2. **Settings → Pages**
    - Source: **Deploy from a branch**
    - Branch: `main`
    - Folder: **`/docs`** — deploy from the `docs` folder so its contents are served at the site root
3. Wait a few minutes for deployment.

Published URLs (repo: `nnnkp/smriti-legal`):

- Home: `https://nnnkp.github.io/smriti-legal/`
- Privacy Policy: `https://nnnkp.github.io/smriti-legal/privacy-policy.html`
- Terms of Service: `https://nnnkp.github.io/smriti-legal/terms.html`

> The files live in `docs/`, but Pages serves that folder at the site root, so the URLs above have **no `/docs/` prefix**. Keep the Pages **Folder** set to `/docs`. If you move the files to the repo root instead, switch the Pages folder to `/ (root)` and the URLs stay the same.

Use the **Privacy Policy** URL in Google Play Console.

## App configuration

The `smriti` app defaults to the URLs above. To override (e.g. a custom domain later), set this in the `smriti` repo's `.env`:

```env
VITE_LEGAL_BASE_URL=https://nnnkp.github.io/smriti-legal
```

Rebuild the app after changing this value. The in-app links are built from this base in `smriti`'s `src/constants/legal.ts`.

## Updating legal text

1. Edit the HTML files in `docs/` in this repo.
2. Commit and push to `main` — Pages redeploys automatically.
3. No app release is required unless you change `VITE_LEGAL_BASE_URL`.
