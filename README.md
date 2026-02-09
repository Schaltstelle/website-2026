# Schaltstelle Website

Static website for [schaltstelle.ch](https://schaltstelle.ch).

The site lives in `docs/` because GitHub Pages only supports serving from `/` (root) or `/docs`. This keeps repo-level files like `AGENDTS.md` and `README.md` out of the public URL.

## Structure

```
docs/                   # Served by GitHub Pages
  index.html            # Main page
  impressum.html        # Legal notice
  datenschutz.html      # Privacy policy
  style.css             # All styles
  fonts/                # Self-hosted Open Sans
  images/
    logos/              # Company logos, favicons
    members/            # Team member photos (400x400 jpg)
    clients/            # Client logos
    community/          # Community partner logos
    services/           # Service icons
    animations/         # Service animation videos (600x600 mp4)
```

## Editing with AI

Example prompts:

**Add a new team member:**
> Add a new member "Anna Müller", role "Software Engineer", with description "...". I put her photo in docs/images/members/.

**Add a new client logo:**
> Add [Company] to the client carousel. I put their logo in docs/images/clients/.

**Add a community partner:**
> Add [Organization] (https://example.ch) to the community section. I put their logo in docs/images/community/.

**Update content:**
> Change the hero text to "..."

## Image guidelines

- Member photos: 400×400px JPG
- Client logos: PNG or SVG, keep file names clean
- Animation videos: 600×600px MP4, H.264, no audio

## High contrast mode

The site includes a contrast-optimized viewing mode for better readability. It increases text contrast, removes opacity reductions, and disables the grayscale filter on client logos.

**How it activates:**

- **Automatically** for users whose OS or browser has a high-contrast preference enabled (`prefers-contrast: high` media query).
- **Manually for testing:** Open the browser DevTools, select the `<html>` element, and add the class `high-contrast`. All the same overrides apply.

**How it works:**

- All contrast overrides live in the "High Contrast Mode" section at the end of `style.css`.
- Two parallel rule sets exist: a `@media (prefers-contrast: high)` block for automatic activation, and `html.high-contrast` selectors for manual testing. Both must stay in sync.

## Compressing assets

**Resize a member photo (macOS built-in):**
```bash
sips -Z 400 docs/images/members/new-photo.jpg
```

**Re-encode a JPEG with quality 80%:**
```bash
sips -s format jpeg -s formatOptions 80 docs/images/members/photo.jpg --out docs/images/members/photo.jpg
```

**Optimize a video (requires `brew install ffmpeg`):**
```bash
ffmpeg -i input.mp4 -vf "scale=600:600" -c:v libx264 -preset slow -crf 23 -an -movflags +faststart output.mp4
```
