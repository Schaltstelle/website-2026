# Schaltstelle Website

Static website for [schaltstelle.ch](https://schaltstelle.ch).

## Structure

```
index.html          # Main page
impressum.html      # Legal notice
datenschutz.html    # Privacy policy
style.css           # All styles
images/
  logos/            # Company logos, favicons
  members/          # Team member photos (400x400 jpg)
  clients/          # Client logos
  community/        # Community partner logos
  services/         # Service icons
  animations/       # Service animation videos (600x600 mp4)
```

## Editing with AI

Example prompts:

**Add a new team member:**
> Add a new member "Anna Müller", role "Software Engineer", with description "...". I put her photo in images/members/.

**Add a new client logo:**
> Add [Company] to the client carousel. I put their logo in images/clients/.

**Add a community partner:**
> Add [Organization] (https://example.ch) to the community section. I put their logo in images/community/.

**Update content:**
> Change the hero text to "..."

## Image guidelines

- Member photos: 400×400px JPG
- Client logos: PNG or SVG, keep file names clean
- Animation videos: 600×600px MP4, H.264, no audio

## Compressing assets

**Resize a member photo (macOS built-in):**
```bash
sips -Z 400 images/members/new-photo.jpg
```

**Re-encode a JPEG with quality 80%:**
```bash
sips -s format jpeg -s formatOptions 80 images/members/photo.jpg --out images/members/photo.jpg
```

**Optimize a video (requires `brew install ffmpeg`):**
```bash
ffmpeg -i input.mp4 -vf "scale=600:600" -c:v libx264 -preset slow -crf 23 -an -movflags +faststart output.mp4
```
