# Freecash Pre-Lander

A high-converting affiliate pre-lander for Freecash — designed to warm up ad traffic before the final signup click.

## Deploy to Vercel (2 minutes)

### Option A — Vercel CLI (fastest)
```bash
npm i -g vercel
cd freecash-lander
vercel
```
Follow the prompts. Your site will be live at a `.vercel.app` URL instantly.

### Option B — Drag & Drop (no code)
1. Go to https://vercel.com/new
2. Click **"Deploy without a Git repository"**
3. Drag the entire `freecash-lander` folder into the upload zone
4. Hit **Deploy** — live in ~30 seconds

### Option C — GitHub (recommended for ongoing edits)
1. Push this folder to a GitHub repo
2. Go to https://vercel.com/new → Import your repo
3. Vercel auto-detects static and deploys

## Custom Domain
After deploying, go to your project in Vercel → **Settings → Domains** → add your domain.

## Customization

### Change your affiliate link
Find and replace `https://trk.dealsforeal.com/click` in `index.html` with your tracking URL.

### Add Google Analytics
Paste your GA4 script before `</head>`:
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXX');
</script>
```

### Add Facebook Pixel
Paste your pixel code before `</head>`.

### UTM passthrough (optional)
To forward UTM params from your ad to the Freecash link, replace the CTA links with:
```html
<a href="#" onclick="passUTM(this, 'https://trk.dealsforeal.com/click'); return false;">
```
And add this script:
```js
function passUTM(el, base) {
  const params = new URLSearchParams(window.location.search);
  window.location.href = base + (params.toString() ? '?' + params.toString() : '');
}
```

## Files
- `index.html` — The full landing page (single file, no dependencies)
- `vercel.json` — Vercel deployment config with security headers + caching
