# GitHub Integration with Cloudflare Pages

This guide shows how to set up automatic deployments from GitHub to Cloudflare Pages for the deltafarce.win root domain.

## Setup Instructions

### 1. Connect GitHub Repository to Cloudflare Pages

1. Go to [Cloudflare Dashboard → Pages](https://dash.cloudflare.com/?to=/:account/pages)
2. Click on the **deltafarce-landing** project
3. Click on **Settings** tab
4. Scroll to **Builds & deployments** section
5. Click **Connect to Git**

### 2. Authorize GitHub

1. Click **Connect GitHub**
2. Authorize Cloudflare Pages (if not already done)
3. Select the repository: `jscrobinson/deltafarce-landing`
4. Click **Install & Authorize**

### 3. Configure Build Settings

This is a **static site** with no build step:

| Setting | Value |
|---------|-------|
| **Framework preset** | None |
| **Build command** | *(leave empty)* |
| **Build output directory** | `/` |
| **Root directory** | `/` (leave empty) |

### 4. Production Branch

- **Production branch**: `main`
- Every push to `main` → Automatic deployment to deltafarce.win

## How It Works

```
git push origin main
    ↓
GitHub webhook triggers Cloudflare
    ↓
Cloudflare deploys files directly (no build needed)
    ↓
Updates https://deltafarce-landing.pages.dev
    ↓
Updates custom domain: https://deltafarce.win
```

## Custom Domain Configuration

After connecting GitHub, add custom domain:

1. In project settings, go to **Custom domains**
2. Click **Set up a custom domain**
3. Enter: `deltafarce.win`
4. Cloudflare will configure DNS automatically

## Files Deployed

- `index.html` - Landing page
- `ads.txt` - AdSense verification (accessible at deltafarce.win/ads.txt)
- `wrangler.toml` - Config (not served publicly)
- `.gitignore` - Git config (not served publicly)

## Testing the Setup

1. Make a change to `index.html`
2. Commit and push:
   ```bash
   git add index.html
   git commit -m "Update landing page"
   git push origin main
   ```
3. Watch deployment in Cloudflare Dashboard
4. Visit https://deltafarce.win after deployment completes

## ads.txt Verification

After deployment, verify ads.txt is accessible:
```bash
curl https://deltafarce.win/ads.txt
```

Should return:
```
google.com, pub-8117946503724556, DIRECT, f08c47fec0942fa0
```

---

**Note:** This site has no build process, so deployments are near-instant (just file uploads).
