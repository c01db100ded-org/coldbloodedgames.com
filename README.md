# Coldblooded Games — coldbloodedgames.com

Static home page + legal pages for **Coldblooded Games**. Hosted on
GitHub Pages (free). DNS stays at Squarespace with the owner.

- Home: `index.html` (mobile-first, static HTML/CSS, no framework)
- Privacy / Terms: see `privacy-policy.html` / `terms-license.html` (HOM-257)
- Assets: `assets/` (real game art, resized for web — source in
  `crown-outpost/docs/store/`)

## Preview

```bash
python3 -m http.server 8000
# open http://localhost:8000/
```

Offline-previewable; no build step.

## Images

Real assets used (no generation needed on first build):

| Path | Source |
|---|---|
| `assets/icon-outpost.png` | `crown-outpost/docs/store/icon-512.png` (256px) |
| `assets/feature-outpost.jpg` | `crown-outpost/docs/store/feature-graphic.png` (1024×500) |
| `assets/shot-outpost-*.jpg` | `crown-outpost/docs/store/screenshots/` (800px) |
| `assets/shot-campaign-*.jpg` | `crown-campaign/test_logs/screenshots/` (800px) |

Gaps for future art: see `images-needed.md`.

## Publish

Push to `main` → GitHub Pages deploys. Custom domain set in
**Settings → Pages → Custom domain**: `www.coldbloodedgames.com`.
See HOM-255 §5 for the Squarespace DNS checklist (owner-only step).

## Rules

- Public pages show only **Coldblooded Games** + `support@coldbloodedgames.com`.
  No personal names/emails.
- No legal copy published without owner sign-off.
- Free only — no paid hosting/credits.
