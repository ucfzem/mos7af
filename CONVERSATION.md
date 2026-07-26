# OpenCode Session — Mos7af Quran Reader

**Date:** Sun Jul 26 2026  
**Repo:** https://github.com/ucfzem/mos7af

---

## Project Overview

`mos7af` is a standalone Quran reader web app with instant tafsir for every verse, built as a single `index.html` file deployed on GitHub Pages and Vercel.

**Live URLs:**
- GitHub Pages: https://ucfzem.github.io/mos7af/
- Vercel: https://mos7af.vercel.app/

---

## Features

- 📖 **Quran Reader** — Load any of the 114 surahs with Uthmani script verse text
- 📘 **Instant Tafsir** — Per-verse tafsir via jsDelivr CDN (spa5k/tafsir_api), supporting Muyassar, Ibn Kathir, Saddi, and Tabari
- 📜 **Al-Muhkamat** — Section explaining Quranic unambiguous vs. ambiguous verses
- 📚 **Manhaj as-Salaf** — Classical methodology for Quranic interpretation
- 🌟 **I'jaz & Maqasid** — Quranic miracles and the five objectives of Sharia
- 🔄 **Surah Persistence** — Current surah saved to localStorage + URL hash, persists on refresh
- 📱 **Mobile-friendly** — Responsive design for mobile and desktop

---

## Technical Stack

- Single `index.html` (HTML + CSS + JS, no build tools)
- `vercel.json` for Vercel routing and production config
- Verse text: alquran.cloud API (with jsDelivr CDN fallback)
- Tafsir: jsDelivr CDN → spa5k/tafsir_api (static JSON, no API keys, no Cloudflare)
- Surah names: hardcoded JS array (no network call dependency)

---

## Key Fixes Applied

1. **Tafsir API broke** — `api.alquran.cloud/v1/ayah/.../tafsir/` endpoints return HTTP 500. Switched to jsDelivr CDN (`spa5k/tafsir_api`) which is static, free, and CORS-open.
2. **Surah reset on refresh** — Added localStorage + URL hash persistence so the current surah is remembered across page reloads.
3. **Cloudflare blocking** — `api.quran.com` and `api.qurancdn.com` use Cloudflare, which blocks some mobile browsers. jsDelivr CDN avoids this entirely.

---

## All Links

### Deployment
- GitHub Pages: https://ucfzem.github.io/mos7af/
- Vercel: https://mos7af.vercel.app/
- GitHub Repo: https://github.com/ucfzem/mos7af

### APIs & Services Used
- alquran.cloud (verse text): https://api.alquran.cloud/v1/surah
- alquran.cloud (uthmani script): https://api.alquran.cloud/v1/surah/{number}/quran-uthmani
- jsDelivr (verse fallback): https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions/ara-quranuthmanihaf/{surah}.json
- jsDelivr (tafsir Muyassar): https://cdn.jsdelivr.net/gh/spa5k/tafsir_api@main/tafsir/ar-tafsir-muyassar/{surah}/{ayah}.json
- jsDelivr (tafsir Ibn Kathir): https://cdn.jsdelivr.net/gh/spa5k/tafsir_api@main/tafsir/ar-tafsir-ibn-kathir/{surah}/{ayah}.json
- jsDelivr (tafsir Saddi): https://cdn.jsdelivr.net/gh/spa5k/tafsir_api@main/tafsir/ar-tafseer-al-saddi/{surah}/{ayah}.json
- jsDelivr (tafsir Tabari): https://cdn.jsdelivr.net/gh/spa5k/tafsir_api@main/tafsir/ar-tafsir-al-tabari/{surah}/{ayah}.json

### Models
- Ling 3.0 Flash Free (124B MoE, 256K context): https://openrouter.ai/inclusionai/ling-3.0-flash:free
- Kilo Code (IDE with Ling 3.0 Flash): https://kilo.ai
- Vercel AI Gateway (Ling 3.0 Flash): https://vercel.com/changelog/ling-3-0-flash-is-now-available-on-ai-gateway

### Fonts
- Amiri Quran (Google Fonts): https://fonts.google.com/specimen/Amiri+Quran

---

## Deployment Commands

```bash
# Push to GitHub (triggers GitHub Pages auto-deploy)
git add -A && git commit -m "message" && git push

# Vercel is connected via GitHub integration — pushes auto-deploy to Vercel
```

---

## Session History

| Step | What |
|------|------|
| 0 | OpenCode session interrupted by sleep/DeepSeek shutdown |
| 1 | Initial HTML file created with tabs: reader, muhkamat, manhaj, ijaz |
| 2 | Deployed to GitHub Pages and Vercel |
| 3 | Fixed tafsir API — alquran.cloud tafsir endpoints return 500; switched to quran.com API |
| 4 | Fixed again — quran.com/qurancdn.com use Cloudflare, blocked by some mobile browsers |
| 5 | Deployed with local tafsir.json for same-origin fetching |
| 6 | Implemented surah persistence via localStorage + URL hash |
| 7 | Final rewrite: hardcoded surah names, jsDelivr CDN for both verses and tafsir |
| 8 | Deployed final version — confirmed working on both GitHub Pages and Vercel |
