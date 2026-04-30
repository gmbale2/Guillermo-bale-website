# guillermobale.com

Personal site of Guillermo Bale — marketing strategist, film producer, SCORE Los Angeles business mentor.

Static HTML/CSS/JS. No build step. Hosted on GitHub Pages with custom domain `guillermobale.com`.

## File structure

```
.
├── index.html        # full page
├── 404.html          # custom 404
├── robots.txt        # crawl directives
├── sitemap.xml       # sitemap with image extensions
├── CNAME             # GitHub Pages custom domain
├── .nojekyll         # tells Pages to skip Jekyll processing
└── assets/
    ├── guillermo-bale-portrait-{600,1200}.webp
    ├── poster-{killhergoats,fogcity,rotld}-{480,960}.webp
    └── og-image.jpg  # 1200×630 social card
```

## Deploy to GitHub Pages

1. **Create the repo** on GitHub, public, name it `guillermobale.com` (any name works — `guillermobale.github.io` would serve at the username URL but we override with CNAME).

2. **Push these files** to the repo's default branch (`main`):
   ```bash
   cd guillermo-website
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin git@github.com:<your-username>/<repo>.git
   git push -u origin main
   ```

3. **Enable Pages**: repo → Settings → Pages →
   - Source: **Deploy from a branch**
   - Branch: `main` / `/ (root)` → Save
   - Custom domain: `guillermobale.com` → Save
   - Wait until the green checkmark, then tick **Enforce HTTPS**.

4. **Point DNS at your registrar** for `guillermobale.com`:
   - **A** records on apex (`@`) to GitHub's four IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - **CNAME** for `www` → `<your-username>.github.io`
   - DNS propagation usually completes in 15 min – 24 h. GitHub will issue a Let's Encrypt cert automatically once it sees the records.

5. **Verify**:
   - https://guillermobale.com loads the site
   - https://www.guillermobale.com redirects to apex
   - PageSpeed Insights / Lighthouse: aim 95+ on all four
   - Google Search Console → submit sitemap: `https://guillermobale.com/sitemap.xml`

## Local dev

Just open `index.html` in a browser — but image paths are relative, so any static server is fine:
```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Editing content

The file is a single hand-written `index.html`. Search for the section text and edit in place. Image paths and dimensions live alongside each `<picture>` block.
