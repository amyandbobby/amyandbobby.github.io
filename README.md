# Save the Date

Two single-screen wedding save-the-date pages for phone and desktop. Each opens with a short Three.js intro and settles on the card.

| Page | Design |
| --- | --- |
| [`noir.html`](noir.html) | Black & white. A projector beam and silver dust form the date, then the screen develops from black to paper like a print. |
| [`floral.html`](floral.html) | Floral, in sand, dusty rose, terracotta, sage and olive. 3D petals blow in, gather into a wreath around the names, then part to reveal the arched garden photo. |
| [`index.html`](index.html) | An overview with both designs side by side. Guests don't need it. |

![Black & white on a phone](previews/noir-phone.jpg) ![Floral on a phone](previews/floral-phone.jpg)

## Preview locally

The pages load their photos as WebGL textures, so open them through a local server rather than straight from disk:

```bash
python3 -m http.server 8420
```

Then visit http://localhost:8420/.

Two URL options help when checking the intro: `?skip=1` shows the finished card straight away, and `?t=3.5` freezes the intro at 3.5 seconds.

## Edit the details

The names, date, venue and calendar event live in the `CONFIG` block near the top of each page's first script. Change them there.

The couple's photo is `assets/amy-bobby-bw.jpg` (black & white, cropped close on the couple) and `assets/amy-bobby.jpg` (floral, full colour). To use a different photo, replace those files (3:4, 1356 × 1808) or point `CONFIG.photo` at a new file. The other images in `assets/` are AI-generated spares from the original template.

## Publish

Any static host works (Netlify, Vercel, Cloudflare Pages, or GitHub Pages, which needs a paid GitHub plan for a private repository). Before sharing:

- Make the `og:image` and `twitter:image` tags absolute, and set `og:url`, so link previews show the card. Both pages mark the spot with a comment.
- Opened normally, "Add to calendar" downloads an `.ics` file. Inside a frame (an embed or a shared preview), where downloads are blocked, it opens Google Calendar instead.

Both pages respect `prefers-reduced-motion` and fall back to the plain card if WebGL or the CDN is unavailable.
