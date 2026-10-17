# dawn-liens

The DAWN AEROWAR link page ("link in bio" for Instagram and the other networks).
One static page: `index.html` + `style.css` + `assets/`. No framework, no build step, no JavaScript, no trackers, nothing loaded from another site.

```
index.html                  the page, with every link in one marked block
style.css                   all layout, colours and motion
assets/
  keyart-vertical.jpg       key art for phones (placeholder)
  keyart-wide.jpg           key art for tablets, desktop and phones held sideways (placeholder)
  favicon.svg               browser tab icon
  apple-touch-icon.png      home-screen icon (iOS)
  fonts/saira-var.woff2     Saira, self-hosted (Latin subset, weights 400–700, widths 100–125 %)
  fonts/OFL.txt             the font's licence
```

## Preview locally

Double-click `index.html`; it opens in your browser. That's all.

For a preview that behaves exactly like the hosted page, serve the folder instead, then open http://localhost:8000:

```sh
python3 -m http.server 8000
```

(When opened straight from disk, Chrome prints a harmless console message about the font *preload*. The font still loads; online the message goes away.)

## Change a link

Open `index.html` and find the block between `LINKS START` and `LINKS END`. There is one line per link:

```html
<li><a class="link" href="https://discord.gg/7DKcN7K8k5"><svg class="icon" aria-hidden="true"><use href="#i-discord"></use></svg>Discord</a></li>
```

- To change where it goes, edit `href="…"`.
- To change what it says, edit the text before `</a>`.
- To add a link, copy a line and change both. The icon is picked by `#i-…`: available icons are `i-website`, `i-discord`, `i-instagram`, `i-x`, `i-facebook`, `i-youtube` (and `i-steam`, used by the big button).
- To remove a link, delete its line.

The big "Wishlist on Steam" button is the `<a class="cta" …>` line at the top of the same block. Nothing else in the page needs touching: the layout adapts to however many links there are.

The links are kept in the HTML rather than in a `links.json` on purpose: a JSON file would need JavaScript to show the links, and browsers refuse to read it when the page is opened from disk. This way the page works everywhere, even without JavaScript.

## Swap the key art

The two images in `assets/` are placeholders. To use the real art, **replace the files and keep the same names**:

| File | Shown on | Recommended |
|---|---|---|
| `assets/keyart-vertical.jpg` | phones held upright | portrait, 1080 × 1920 (9:16) or 1080 × 1350 (4:5) |
| `assets/keyart-wide.jpg` | tablets, computers, phones held sideways | landscape, 2560 × 1440 (16:9) |

Then:

1. **Size and weight.** Export as JPEG at quality ~80, ideally under 300 KB each (most visitors are on mobile data).
2. **Dimensions.** If your files are not 1080 × 1920 and 2560 × 1440, update the `width`/`height` numbers on the `<source>` and `<img>` lines in `index.html`. They only describe the files' proportions; the layout doesn't depend on them.
3. **Alt text.** Update the `alt="…"` text on the `<img>` line so it describes the real art (it is read aloud by screen readers).
4. **Framing.** The art is cropped to fill the top of the page, and its lower part is darkened so the title stays readable. Keep the important part of the art in the upper two thirds. To change which part stays in frame, edit these two lines at the top of `style.css` (horizontal %, then vertical %):

   ```css
   --art-focus-vertical: 50% 50%;   /* e.g. 50% 30% keeps more of the top */
   --art-focus-wide: 50% 50%;
   ```

## Before it goes live

- Add a social preview image: once the final address is known, add `<meta property="og:image" content="https://dawnaerowar.com/…/keyart-wide.jpg">` and `<meta property="og:url" content="https://dawnaerowar.com/…">` in the `<head>` (both need full addresses starting with `https://`).
- Replace the placeholder key art (see above).
- Upload the whole folder as-is: `index.html`, `style.css` and `assets/` must stay side by side.

## What is built in

- **Mobile first.** Designed for 360 px wide phones first; checked from 320 px to 1440 px, upright and sideways. The Steam button sits in the first screen on phones.
- **Fast.** About 70 KB without images (HTML 6 KB, CSS 15 KB, font 49 KB), around 56 KB once compressed by the server.
- **Accessible.** Real links in a logical order; text contrast of 7:1 or more (the big title stays above 5:1 even over the brightest part of the art, above the 4.5:1 that large text needs); a clear focus outline for keyboard users; alt text on the key art; full support for Windows high-contrast mode.
- **Motion with restraint.** On load, the art settles, the dawn light rises and the content fades up; it all finishes in under 3 seconds and nothing loops. Visitors who ask their device to reduce motion get a still page.

## Credits

- Typeface: [Saira](https://github.com/Omnibus-Type/Saira) by Omnibus-Type, SIL Open Font License 1.1 (`assets/fonts/OFL.txt`).
- Icons: [Tabler Icons](https://tabler.io/icons) (MIT License, © Paweł Kuna) and the Steam mark from [Simple Icons](https://simpleicons.org) (CC0). Brand logos belong to their owners.
- Placeholder key art: made for this page (procedural, no photo or third-party material).
