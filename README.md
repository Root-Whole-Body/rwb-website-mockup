---
type: runbook
date: 2026-10-14
project: brand-optimization-leveraged-revenue
department: Marketing, Brand & Community Growth
status: draft
tags: [website, deploy, wholebodyhealth-xyz, cloudflare-pages, noindex]
---

## What this folder is

A static, hidden copy of the new Home page for the [[website-redesign-plan]], built from the Figma "Home v3" frame (Bridget's preferred Figma design, in the Figma brandbook palette) and the copy in [[website-copy-v2]]. It is meant for `wholebodyhealth.xyz` only. It never touches `rootwholebody.com`.

## Files

| File | Job |
|---|---|
| `index.html` | The whole page, one file, no build step |
| `images/` | Six photos exported from Figma (low resolution, swap for originals before launch) |
| `robots.txt` | Tells search engines to stay out |
| `_headers` | Sends a noindex header on every file (works on Cloudflare Pages and Netlify) |

The page also has a noindex meta tag and an orange banner that says it is a private mockup. Remove the banner when it is no longer a mockup. Text in [brackets] is a fact still to confirm, see the last table in [[website-copy-v2]].

> [!warning] Fonts
> Titles use PP Editorial New Ultralight in the design. It is a licensed font, so the page falls back to Instrument Serif (free) until the licensed web font files are added to a `fonts/` folder and an `@font-face` rule. Body font Figtree loads from Google Fonts.

## Deploy steps (about 15 minutes)

1. Create a free Cloudflare Pages account with a Root email address (not a personal one, per [[rwb-infrastructure-ownership]]). Name the project `rwb-website-mockup`.
2. Create a new project, choose "Direct Upload", and upload this whole `site` folder.
3. In the project, open Custom domains and add `wholebodyhealth.xyz`.
4. Cloudflare then shows one DNS record to add (a CNAME to the `*.pages.dev` address). In GoDaddy, open DNS for `wholebodyhealth.xyz`, add that record, and save. Do not touch any `rootwholebody.com` record.
5. Wait for the certificate (usually under 10 minutes), then open `https://wholebodyhealth.xyz`.
6. Check: the orange banner shows, view-source has `noindex`, and `https://wholebodyhealth.xyz/robots.txt` says `Disallow: /`.

> [!important] Before sharing the link outside Root
> Turn on Cloudflare Access (free for a few people) or a password on the project, so only people you invite can see it. A noindex tag keeps Google out but does not keep people out.

## Preview on this Mac

```bash
cd Projects/brand-optimization-leveraged-revenue/site
python3 -m http.server 8811
```

Then open `http://127.0.0.1:8811/index.html`.
