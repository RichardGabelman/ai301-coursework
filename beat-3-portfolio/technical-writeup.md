# Basic website configuration for the AI age (robots.txt + page meta in the era of increasing intelligent robots!)

## Overview

https://github.com/lolimmlost/aidj/pull/418

Adds `public/robots.txt` with rules disallowing everything but:
- the landing page (`/$`)
- `/assets/` (Google renders pages, and if it can't load these the landing page looks empty or broken to it)
- `/og-image.png` (for social previews)
- `/favicon.ico`, `/icons/`, `/manifest.json` (Favicon and PWA metadata that search results and browsers show next to the site)
- `/music-identity/share/` (public share links which need to be fetchable for link previews)
- `/playlists/join/` (same reasoning)
- `/invite` (same reasoning)

Adds `noindex` to the root head.

Adds `index, follow` override to the landing page.

I have a PR open, awaiting review/merging.

## What happened

### Before:

#### 1. robots.txt: not served

curl -si localhost:3006/robots.txt → HTTP/1.1 404, content-type: text/html; charset=utf-8

The request falls through to the app's HTML 404 page, so crawlers get no rules at all.

#### 2. Robots meta tags in SSR output

┌──────────────────────────────┬──────────────────────────────────────────────────┬────────────┬──────────────────┐
│             Path             │                      Status                      │  robots    │  og:/twitter:    │
│                              │                                                  │    meta    │       tags       │
├──────────────────────────────┼──────────────────────────────────────────────────┼────────────┼──────────────────┤
│ /                            │ 200                                              │ none       │ present          │
├──────────────────────────────┼──────────────────────────────────────────────────┼────────────┼──────────────────┤
│ /login                       │ 200                                              │ none       │ present          │
├──────────────────────────────┼──────────────────────────────────────────────────┼────────────┼──────────────────┤
│ /music-identity/share/abc123 │ 200                                              │ none       │ present          │
├──────────────────────────────┼──────────────────────────────────────────────────┼────────────┼──────────────────┤
│ /invite                      │ 200                                              │ none       │ present          │
├──────────────────────────────┼──────────────────────────────────────────────────┼────────────┼──────────────────┤
│ /dashboard                   │ 307 → /login?redirect=%2Fdashboard               │ n/a        │ n/a              │
├──────────────────────────────┼──────────────────────────────────────────────────┼────────────┼──────────────────┤
│ /playlists/join/abc123       │ 307 →                                            │ n/a        │ n/a              │
│                              │ /login?redirect=%2Fplaylists%2Fjoin%2Fabc123     │            │                  │
└──────────────────────────────┴──────────────────────────────────────────────────┴────────────┴──────────────────┘

#### 3. Existing checks

- npx vitest run → Test Files 85 passed | 3 skipped (88), Tests 1041 passed | 26 todo (1067)
- npm run lint → 0 errors, 392 warnings
- npm run build → exit 0, ✓ built

### After:

#### 1. `public/robots.txt` is served

`curl -si localhost:3004/robots.txt` → `HTTP/1.1 200 OK`, `Content-Type: text/plain`

```
User-agent: *
Allow: /$
Allow: /assets/
Allow: /og-image.png
Allow: /favicon.ico
Allow: /manifest.json
Allow: /icons/
Allow: /music-identity/share/
Allow: /playlists/join/
Allow: /invite
Disallow: /
```

#### 2. Robots meta tags in SSR output

Command: `curl -s localhost:3005<path> | grep -oE '<meta [^>]*>' | grep -E 'robots|og:|twitter:'`

| Path | Status | robots meta | og:/twitter: tags |
|------|--------|-------------|-------------------|
| `/` | 200 | `index, follow` (only one robots tag — the route override replaces the root `noindex`) | present |
| `/login` | 200 | `noindex` | present |
| `/music-identity/share/abc123` | 200 | `noindex` | present (og:title, og:description, og:image, twitter:card, twitter:image, …) |
| `/invite` | 200 | `noindex` | present |
| `/dashboard` | 307 → `/login?redirect=%2Fdashboard` | n/a (unauthenticated) | n/a |
| `/playlists/join/abc123` | 307 → `/login?redirect=…` | n/a (unauthenticated) | n/a |

Example (`/music-identity/share/abc123`):

```html
<meta name="robots" content="noindex"/>
<meta property="og:title" content="AIDJ"/>
<meta property="og:description" content="AI-powered music discovery and smart playlists"/>
<meta property="og:image" content="http://localhost:3000/og-image.png"/>
<meta name="twitter:card" content="summary_large_image"/>
<meta name="twitter:image" content="http://localhost:3000/og-image.png"/>
```

The share route defines no `head()` of its own, so its tags come from the root route. A real share token would render the same `<head>` as the dummy token used here.

#### 3. Existing checks

- `npx vitest run` → `Test Files 85 passed | 3 skipped (88)`, `Tests 1041 passed | 26 todo (1067)`
- `npm run lint` → `0 errors, 392 warnings`. The only warning in a changed file (`src/routes/__root.tsx:35`, `ensureQueryData` deprecated) is on a line this PR did not touch.
- `npm run build` → exit 0, `✓ built`


## Limitations and what's next

I think these additions probably could have been separated into two separate issues/PRs: robots.txt, and the meta noindex besides on the landing page. Directionally related in that both deal with instructions to webcrawlers and the like, but via different mechanisms in different files. The counter point to that would be that the robots.txt naive implementation would have a higher chance of going through without the added issue context of the shareable link tags needing to remain, alas. 

I think this level of 'testing' goes a bit overboard given the scope of changes (and frankly the scope of the project). Without AI to handle determining the correct command line commands and handling the formatting, I would not have bothered (and I don't think it would have been missed in any typical pr review).