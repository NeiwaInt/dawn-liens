# DAWN AEROWAR: link page (homemade "linktree")

One static, responsive landing page that gathers every DAWN AEROWAR link, for the "link in bio" of Instagram and the other networks.
It will be hosted later under dawnaerowar.com (path to be decided). Nothing here is published until the owner gives his go.

## What it must be
- Pure static HTML + CSS (+ a few lines of vanilla JS at most), no framework, no build step, no tracking, no third-party fonts or scripts loaded from a CDN (fonts self-hosted or system stack).
- Beautiful and cinematic, in DAWN's look: dark sky, warm amber dawn light, clean military-aviation typography feeling, without any real aircraft, ship or manufacturer name.
- Mobile first (most visits come from Instagram on a phone), perfect at 360 px wide, also good on desktop. Fast: under 200 KB without images.
- Accessible: real links, readable contrast, focus styles, alt text, works without JS.

## Content, top to bottom
1. Key art (vertical on phone, wide on desktop): use `assets/keyart-vertical.jpg` and `assets/keyart-wide.jpg` (placeholders: the real files are added later; keep the paths). Title "DAWN AEROWAR" and the line "An animated film in twelve episodes".
2. The main button, big and first: "Wishlist on Steam" -> https://store.steampowered.com/app/2991650/
3. Then: Official website https://dawnaerowar.com/ ; Discord https://discord.gg/7DKcN7K8k5 ; Instagram https://www.instagram.com/dawnaerowar/ ; X https://x.com/DawnAerowar ; Facebook https://facebook.com/DawnAerowar ; Original soundtrack on YouTube https://www.youtube.com/@josepavli
4. Footer: "© Neiwa Interactive" (the company publishing DAWN AEROWAR). No personal names.

Keep every link in one small `links.json` (or a clearly marked block at the top of the HTML) so links can be changed without touching the layout.

## Deliverable
`index.html`, `style.css`, `links.json` if used, an `assets/` folder with placeholders, and `README.md` saying how to preview it locally (open index.html) and how to swap the key art. Commit on your own branch only.
