# Vancouver Island Grand Loop — Project Brief

## What this is
A static website for the VIGL (Vancouver Island Grand Loop), an adventure motorcycle route circumnavigating Vancouver Island. 1,700 km, 18 stages.

## Live site
- URL: https://vancouverislandgrandloop.com
- GitHub repo: https://github.com/link7373/vigl-site (branch: master)
- GitHub Pages — custom domain via CNAME file, HTTPS enforced

## Local development
```bash
cd C:/Claude/VIGL
python -m http.server 8080
# → http://localhost:8080
```
Use `nohup python -m http.server 8080 > /tmp/vigl-server.log 2>&1 &` to keep it running.  
Use `python` not `python3` on this machine.  
Use Windows-style paths (`C:/Claude/VIGL`) not Git Bash paths (`/c/Claude/VIGL`) in Python scripts.

## File structure
```
C:/Claude/VIGL/
  index.html, about.html, faq.html, stages.html   ← root pages
  stages/stage-1.html … stage-18.html             ← 18 stage pages
  styles.css                                        ← single stylesheet
  favicon.svg                                       ← diamond mark
  vigl-mark.svg                                    ← logo mark only
  vigl-lockup.svg                                  ← horizontal lockup (light)
  vigl-lockup-dark.svg                             ← horizontal lockup (dark bg)
  sitemap.xml
  CNAME                                            ← vancouverislandgrandloop.com
  photos/                                          ← local stage photos (Stage N - *.jpg)
```

## Brand
**Colours**
- Red: `#c4402a`
- Ink (dark): `#1c1b18`
- Cream (bg): `#faf6ef`
- Mustard: `#d4982a`
- Border: `#d8d0c4`

**Fonts** (Google Fonts)
- Headings: `Archivo Black`
- Body/subheads: `Barlow Condensed` (600/700) + `Barlow` (400/500)
- Mono accents: `IBM Plex Mono`

## Logo system
- **Mark** (`vigl-mark.svg`): 200×200 red diamond, cream mountain outline at 50% opacity, VIGL text at bottom
- **Lockup light** (`vigl-lockup.svg`): 370×105 — mark + VIGL wordmark + Vancouver Island Grand Loop + rule + Est 2015 (for light backgrounds)
- **Lockup dark** (`vigl-lockup-dark.svg`): same layout, cream text (for dark/footer backgrounds)
- **Nav**: inline mark SVG at 44px + `.nav-logo-text` span ("Vancouver Island Grand Loop")
- **Footer**: inline dark lockup SVG at 56px height

## Nav logo HTML pattern (root pages)
```html
<a class="nav-logo" href="index.html">
  <svg class="nav-mark" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200">
    ... mark content ...
  </svg>
  <span class="nav-logo-text">Vancouver Island<br>Grand Loop</span>
</a>
```
Stage pages use `href="../index.html"` and the footer uses `class="footer-logo"` with the dark lockup SVG.

## Key CSS classes
- `.nav-mark` — 44px inline SVG in nav
- `.nav-logo-text` — text beside nav mark (hidden on mobile ≤600px)
- `.footer-logo` / `.footer-lockup` — footer lockup container + SVG

## Deploy
```bash
cd C:/Claude/VIGL
git add <files>
git commit -m "message"
git push origin master
```
GitHub Pages auto-deploys in ~1 min. Do NOT push until owner approves local preview.

## What's been built
- All 18 stage pages with route info, photos, stats
- Homepage (hero, route overview, stage grid, CTA)
- About, FAQ, Stages index pages
- Custom diamond VIGL logo designed and implemented
- Sitemap.xml, favicon, DNS cutover to GoDaddy, HTTPS live

## Stage photos
Local photos live in `C:/Claude/VIGL/photos/` named `Stage N - description.jpg`.  
Injection script: `inject_photos_local.py` — run if photos need to be re-injected.
