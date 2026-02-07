# Agent Guidelines

## Project overview

Static website for schaltstelle.ch, a small IT consulting company in Bern. Pure HTML, CSS, and vanilla JavaScript — no build step.

The site is served from `docs/` via GitHub Pages.

## Rules

- **No frameworks or libraries** without asking the user first. No Tailwind, no Bootstrap, no jQuery, no React. Custom CSS only.
- **All three HTML pages must stay in sync.** Changes to the header, footer, navigation, meta tags, or shared structure must be applied to `index.html`, `impressum.html`, and `datenschutz.html`.
- **Optimize images before committing.** Member photos: 400×400px JPG (use `sips -Z 400`). Client/community logos: keep file sizes reasonable. Videos: 600×600px MP4 H.264 (use `ffmpeg`). See `README.md` for exact commands.
- **Update README.md** with any structural changes worth remembering (new sections, new asset directories, changed conventions).
- **Member photos** are named `<firstname>-<lastname>.jpg`, all lowercase.
- **Client and community logos** should have clean filenames (no dimensions, no URL-encoded characters).
- **Members, clients, and community logos are randomly shuffled** on page load via JavaScript. Order in the HTML doesn't matter.

## File layout

```
docs/
  index.html          # Main single-page site
  impressum.html      # Legal notice (Impressum)
  datenschutz.html    # Privacy policy (Datenschutzerklärung)
  style.css           # All styles (single file)
  fonts/              # Self-hosted Open Sans (woff2)
  images/
    logos/            # Company logos, favicons, webmanifest icons
    members/          # Team member photos (400×400 jpg)
    clients/          # Client logos (png/svg)
    community/        # Community partner logos (png/svg)
    services/         # Service section icons (white on transparent)
    animations/       # Service animation videos (600×600 mp4)
```

## Conventions

- Colors: white `#ffffff`, purple `#221c35`, red `#e6443b`
- Font: Open Sans (self-hosted, no Google Fonts CDN)
- Images below the fold use `loading="lazy"`. Service icons and the header logo do not.
- Videos use `preload="none"` and are played/paused via a scroll listener in JS.
- The site is currently set to `noindex` (meta tag + robots.txt). See README for the go-live checklist.
