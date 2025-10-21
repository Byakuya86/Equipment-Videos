# Quick Deploy Guide

This folder contains your **single-page site** (`index.html`). You can deploy it to your domain in minutes.

## Option A — Netlify (fast + free SSL)
1. Go to Netlify → **Add new site** → **Deploy manually**.
2. **Drag & drop** this folder (the one containing `index.html`) onto the dropzone.
3. Open the temporary URL (e.g. `https://your-site-xyz.netlify.app`) to verify.
4. Netlify → **Site settings** → **Domains** → **Add custom domain** → enter `www.yourdomain.com`.
5. Update DNS at your domain registrar:
   - Create **CNAME** record:  
     - Name/Host: `www`  
     - Value/Target: your Netlify site (e.g., `your-site-xyz.netlify.app`)
6. (Optional) Point apex domain `yourdomain.com` to Netlify (use ALIAS/ANAME or switch to Netlify DNS).
7. In Netlify **Domains**, click **Verify** and enable **HTTPS** (Let’s Encrypt).

## Option B — cPanel/FTP (traditional hosting)
1. Log into **cPanel** → **File Manager**.
2. Go to `public_html/` and upload `index.html` there.
3. Visit `https://yourdomain.com` to verify.
4. If you use client-side routing in future, add this to `.htaccess`:
```
RewriteEngine On
RewriteBase /
RewriteRule ^index\.html$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.html [L]
```

## YouTube Embed (replace the placeholder)
Find the block:
```html
<div class="video-placeholder">
  [YouTube Video Embed Here]
</div>
```
Replace it with your iframe, e.g.:
```html
<div style="position:relative;padding-bottom:56.25%;height:0;overflow:hidden;border-radius:8px;">
  <iframe src="https://www.youtube.com/embed/VIDEO_ID" title="Mark 3 Pump Training"
    frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
</div>
```

## Documentation buttons
Replace `href="#"` with the actual file URLs (e.g., PDFs). If the files live in the same folder, place them next to `index.html` and set:
```html
<a class="download-btn" href="Operator_Manual.pdf" download>📕 Operator Manual</a>
```

## QR Codes
- Generate a QR code that encodes **your final page URL** (e.g., `https://www.yourdomain.com/pump/mark3/`).
- If you **update the page** but **keep the same URL**, you **do not need a new QR code**.
- Only if the **URL changes** do you need to print a new QR label.

## Notes
- Ensure the published directory contains `index.html` at the root.
- Avoid absolute asset paths; use relative paths like `./file.pdf`.
