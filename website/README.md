# LockLoom Website — lockloom.app

Production website for LockLoom Secure Access Platform.

## Structure

```
website/
├── index.html          # Main landing page (marketing + docs)
├── languages.html      # 144 locales with completion status
├── privacy.html        # Privacy policy
├── provisioning.html   # Device Owner QR provisioning page
├── css/
│   ├── style.css       # Main stylesheet
│   └── policy.css      # Policy/legal page styles
├── js/
│   └── main.js         # Interactions (nav, FAQ accordion, scroll effects)
├── _headers            # Cloudflare security headers
├── _redirects           # Cloudflare redirect rules
└── img/                # Local images (app icon served from GitHub Pages CDN)
```

---

## Deploying to Cloudflare Pages (Step-by-Step)

### Option A: Direct Upload (Easiest — No Git Required)

1. **Log in** to [dash.cloudflare.com](https://dash.cloudflare.com)
2. In the left sidebar, click **"Workers & Pages"**
3. Click the **"Create"** button (top right)
4. Select the **"Pages"** tab
5. Click **"Upload assets"** (skip the Git option)
6. **Name your project**: type `lockloom-app` and click "Create project"
7. **Upload**: Drag the entire `website/` folder into the upload area  
   *(Or click "Select from computer" and select all files inside `website/`)*
8. Click **"Deploy site"** — wait ~30 seconds
9. Cloudflare gives you a URL like `lockloom-app.pages.dev` — your site is live!

### Option B: Connect to GitHub (Auto-deploys on push)

1. **Log in** to [dash.cloudflare.com](https://dash.cloudflare.com)
2. Go to **Workers & Pages** → **Create** → **Pages** tab
3. Click **"Connect to Git"**
4. Select your GitHub account and the **LockLoom** repository
5. Configure build settings:
   - **Framework preset**: `None`
   - **Build command**: *(leave empty)*
   - **Build output directory**: `website`
   - **Root directory**: `/`
6. Click **"Save and Deploy"**
7. Every time you push to main, Cloudflare auto-redeploys

### Adding Your Custom Domain (lockloom.app)

After deploying (either Option A or B):

1. Go to **Workers & Pages** → click your `lockloom-app` project
2. Click the **"Custom domains"** tab
3. Click **"Set up a custom domain"**
4. Type `lockloom.app` and click **"Continue"**
5. Cloudflare will auto-configure DNS (since you already own the domain on Cloudflare)
6. Wait 1-2 minutes for SSL to provision — done!
7. *(Optional)* Also add `www.lockloom.app` — it will auto-redirect

### Option C: Wrangler CLI (Command Line)

If you prefer the terminal:

```powershell
# Install Wrangler (one time)
npm install -g wrangler

# Log in to Cloudflare
wrangler login

# Deploy (run from the repo root)
npx wrangler pages deploy ./website --project-name=lockloom-app
```

After first deploy, add the custom domain via the dashboard (same steps as above).

---

## GitHub Pages (docs mirror)

The docs/policies are also available at `lockloom-llc.github.io/LockLoom/`.
The main site links to GitHub Pages for:
- Device Owner Policies HTML
- Play Store icon asset (ic_launcher-playstore-512.png)
- Provisioning QR code PNG

## Design System

- **Theme**: Void-grade dark (executive black aesthetic)
- **Accent**: `#00D4AA` (teal/mint)
- **Font**: Inter (Google Fonts)
- **Responsive**: Mobile-first, breakpoints at 600px and 900px

## Pages

| Page | URL | Description |
|------|-----|-------------|
| Home | `/` | Full marketing landing with features, pricing, distress system, FAQ, docs |
| Languages | `/languages.html` | 144 locales grouped by tier with completion percentages |
| Privacy | `/privacy.html` | Zero-data-collection privacy policy |
| Provisioning | `/provisioning.html` | Device Owner QR code + setup instructions |

## Assets

The app icon and QR code are served from GitHub Pages CDN:
- Icon: `https://lockloom-llc.github.io/LockLoom/assets/ic_launcher-playstore-512.png`
- QR: `https://lockloom-llc.github.io/LockLoom/lockloom-dpc-qr.png`
