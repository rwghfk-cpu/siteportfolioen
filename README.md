# [rwzk] — Portfolio

A single-file portfolio site (`index.html`), no frameworks and no heavy dependencies — loads fast and doesn't lag. It only uses Google Fonts (Baloo 2 + Inter) and a little bit of vanilla JavaScript (just to copy the Discord ID).

Visual style: black background, bold red and blue (Spider-Man-inspired) and a fun, rounded display font (Baloo 2) for the `[rwzk]` name and headings.

## Structure

- **Top (nav):** fixed `[rwzk]` logo + links to "Work" and "Contact".
- **Hero:** the name in a red → blue gradient, two soft blurred glows in the background, and two buttons — "See my work" and "Get in touch".
- **Work:** 5 video slots — 4 in a 2x2 grid + 1 highlight card spanning the full width at the end, with no caption on top for a clean look.
- **Contact:** a list with Discord, Email, and Twitter.

## Adding your real videos

Each video lives inside an `<article class="video-card">`. By default, the site ships with a placeholder (a background with a play icon) in each slot. Swap it for a real video one of two ways:

**Option A — YouTube embed (recommended):**
Replace the `<div class="placeholder">...</div>` block with an iframe, for example:

```html
<article class="video-card">
  <iframe
    src="https://www.youtube.com/embed/YOUR_VIDEO_ID"
    title="Video name"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen>
  </iframe>
</article>
```

Swap `YOUR_VIDEO_ID` for the part that comes after `v=` in the YouTube link.

The 5th card has an extra `destaque` class and spans the full row — it's meant for a compilation, a "best of the year," or whichever video you want to highlight most. If you'd rather drop that highlight and keep all 5 the same size, just remove `class="video-card destaque"` and replace it with `class="video-card"`.

**Option B — Your own video file (mp4):**

```html
<video src="videos/my-video.mp4" controls preload="metadata"></video>
```

In this case, create a `videos/` folder next to `index.html` and put your `.mp4` files there.

## Editing the colors

Colors are centralized at the top of the `<style>` block, inside `:root`:

```css
--bg: #0a0a0c;       /* black background */
--red: #ff2438;      /* main red (Spider-Man-inspired) */
--blue: #3161ff;     /* main blue (Spider-Man-inspired) */
```

Changing these values updates the whole site automatically — including the name's gradient, the hero glows, the button border, the video hover states (odd cards turn red, even ones turn blue), and the contact hover states.

## Changing the font

The name and headings use **Baloo 2** (a fun, rounded font). Body text uses **Inter**. To swap it out:
1. Pick another font at [fonts.google.com](https://fonts.google.com).
2. Update the `<link href="https://fonts.googleapis.com/css2?family=...">` in the `<head>`.
3. Replace `'Baloo 2'` with the new font name in the `h1, h2`, `.logo`, and `.wordmark` rules.

## Editing your contacts

At the end of the file, inside the `<section id="contato">`:
- **Discord:** replace `rw_ofc` with whatever text should show (clicking it already copies that text to the clipboard).
- **Email:** replace the address in `href="mailto:..."` and in the visible text.
- **Twitter:** replace the `href="https://x.com/..."` link and the visible `@handle`.

## Publishing the site (free)

Any of these work well for a single-file site:

1. **GitHub Pages:** create a repo, upload `index.html`, enable Pages in the repo settings.
2. **Netlify / Vercel:** drag and drop the project folder into their deploy area — no setup needed.

## Performance notes

- No external animation libraries or frameworks — just HTML, CSS, and a bit of JS.
- The only blur effect used is on the two background glows at the top and the nav bar's backdrop — light enough to not slow down loading.
- Animates only once, on page load (the name gently rising into place); there's no constant animation running, which keeps things from lagging.
