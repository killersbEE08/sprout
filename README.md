# Sprout — Marketing Website

Static marketing site for **Sprout**, a playful, offline-first habit &amp; wellness app.

No build step, no dependencies — plain HTML + CSS. Hosted on **Cloudflare Pages**.

## Pages

| File                   | URL (clean)        | Purpose                             |
|------------------------|--------------------|-------------------------------------|
| `index.html`           | `/`                | Landing page                        |
| `privacy.html`         | `/privacy`         | Privacy Policy                      |
| `terms.html`           | `/terms`           | Terms of Service                    |
| `delete-account.html`  | `/delete-account`  | Account &amp; data deletion         |
| `support.html`         | `/support`         | Support / contact / FAQ             |
| `404.html`             | (not found)        | Branded 404 page                    |

Shared assets: `styles.css` (design system) and `assets/logo.svg` (brand mark).

`_headers` sets security + caching headers; `_redirects` sends `*.html` to clean paths.

> Cloudflare Pages serves clean URLs automatically — e.g. `privacy.html` is
> reachable at `/privacy` with no extra config.

## Local preview

Any static server works. For example:

```bash
# Python
python -m http.server 8080

# or Node
npx serve .
```

Then open http://localhost:8080. (Note: clean URLs like `/privacy` resolve on
Cloudflare Pages; locally use `/privacy.html` or a server that rewrites.)

## Deploy to Cloudflare Pages

This repo is designed for Git-based continuous deployment.

### 1. Push to GitHub
The code lives at https://github.com/killersbEE08/sprout

### 2. Connect the repo in Cloudflare
1. Go to the Cloudflare dashboard → **Workers &amp; Pages** → **Create** → **Pages** → **Connect to Git**.
2. Authorize GitHub and select the **`sprout`** repository.
3. Configure the build:
   - **Framework preset:** `None`
   - **Build command:** *(leave empty)*
   - **Build output directory:** `/` (repository root)
4. Click **Save and Deploy**. Cloudflare builds and publishes in ~30s.

Every push to the default branch triggers an automatic redeploy.

### 3. Custom domain (sprout.princelabs.me)
1. In the Pages project → **Custom domains** → **Set up a custom domain**.
2. Enter `sprout.princelabs.me`.
3. If `princelabs.me` is on Cloudflare, the DNS `CNAME` is added automatically.
   Otherwise add a `CNAME` for `sprout` pointing to your `*.pages.dev` hostname.

Your legal links will then resolve as:
- https://sprout.princelabs.me/privacy
- https://sprout.princelabs.me/delete-account

## Brand tokens
Purple gradient `#7C4DFF → #9B5DE5`, yellow accent `#FFE14D`, ink `#1b1730`,
background `#faf8ff`. Font: Inter.
