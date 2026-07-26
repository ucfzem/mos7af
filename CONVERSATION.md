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
- 📘 **Instant Tafsir** — Per-ayah tafsir via jsDelivr CDN (spa5k/tafsir_api), supporting Muyassar, Ibn Kathir, Saddi, and Tabari
- 📜 **Al-Muhkamat** — Section explaining Quranic unambiguous vs. ambiguous verses
- 📚 **Manhaj as-Salaf** — Classical methodology for Quranic interpretation
- 🌟 **I'jaz & Maqasid** — Quranic miracles and the five objectives of Sharia
- 🔄 **Surah Persistence** — Current surah saved to localStorage + URL hash, persists on refresh
- 🌗 **Dark Mode** — Toggle between light and dark themes
- 📊 **Progress Bar** — Tracks current position within a surah on scroll
- 📤 **Share** — Share ayahs via Web Share API or clipboard
- 🔖 **Bookmarks** — Save and manage favorite ayahs
- 🔍 **Search** — Filter surahs in the dropdown
- 📱 **Mobile-Optimized** — 44px touch targets, smooth animations, responsive

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
- This conversation: https://github.com/ucfzem/mos7af/blob/main/CONVERSATION.md

### APIs & Services Used
- alquran.cloud (verse text): https://api.alquran.cloud/v1/surah
- alquran.cloud (uthmani script): https://api.alquran.cloud/v1/surah/{n}/quran-uthmani
- jsDelivr (verse fallback): https://cdn.jsdelivr.net/gh/fawazahmed0/quran-api@1/editions/ara-quranuthmanihaf/{n}.json
- jsDelivr (tafsir Muyassar): https://cdn.jsdelivr.net/gh/spa5k/tafsir_api@main/tafsir/ar-tafsir-muyassar/{surah}/{ayah}.json
- jsDelivr (tafsir Ibn Kathir): https://cdn.jsdelivr.net/gh/spa5k/tafsir_api@main/tafsir/ar-tafsir-ibn-kathir/{surah}/{ayah}.json
- jsDelivr (tafsir Saddi): https://cdn.jsdelivr.net/gh/spa5k/tafsir_api@main/tafsir/ar-tafseer-al-saddi/{surah}/{ayah}.json

### Inspiration Reference
- Quran for Android: https://github.com/quran/quran_android

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

## Inspiration from quran_android (https://github.com/quran/quran_android)

Transferable patterns identified for future mos7af enhancements:

1. **Page-based navigation** — navigate by page number (604 pages) alongside surah/ayah
2. **Advanced reading progress** — session tracking, last-read tracking
3. **Bookmark metadata** — tags, notes, colors for bookmarks
4. **Audio/Recitation** — built-in audio player with multiple reciters
5. **Full-text search** — keyword search across verses and translations
6. **Offline caching** — Service Worker for offline access
7. **Translation overlay** — toggleable translations (English, French, etc.)
8. **Reading preferences** — font size slider, line spacing, advanced theme options
9. **ViewModel/StateFlow architecture** — structured state management pattern
10. **Dark mode** — already implemented, could be expanded with more theme options
