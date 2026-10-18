# Convertive UGC website

A plain HTML, CSS and JavaScript site. No build step, no database, no paid services.

```
convertive-ugc/
├── index.html          all page content (text, prices, links)
├── assets/
│   ├── styles.css      colours, fonts, layout
│   ├── main.js         menu + video players
│   ├── favicon.svg
│   └── og-image.jpg    social share image (1200 x 630)
├── videos/             your four MP4 files
└── posters/            the still image shown before each video plays
```

## 1. Preview on your computer

Double-click `index.html`. It opens in your browser and everything works.
(The Bricolage Grotesque font loads from Google Fonts when you are online. Offline, the site falls back to Helvetica/Arial.)

## 2. Replace a video or poster

Each card in `index.html` has a `<video src="..." poster="...">`.

**Easiest way (no code):** save your new files over the old ones with the same names.

| Card | Video | Poster |
|---|---|---|
| Totes Blazin' BBQ Peanut Puffs | `videos/totes-peanut-puffs.mp4` | `posters/totes-peanut-puffs.jpg` |
| Dynamic Fitness Equipment | `videos/dynamic-fitness.mp4` | `posters/dynamic-fitness.jpg` |
| AK Sports Boomstick Red Pickleball Paddle | `videos/ak-sports-pickleball.mp4` | `posters/ak-sports-pickleball.jpg` |
| Fourth card (currently Dark Chocolate Crispy Peanut Butter) | `videos/dark-chocolate-peanut-butter.mp4` | `posters/dark-chocolate-peanut-butter.jpg` |

**To use different file names:** open `index.html`, find the card (search for the product name) and edit `src="..."` and `poster="..."`.

**To show the Feastables ad in the fourth card:**
1. Put the file at `videos/feastables-motion-ad.mp4` and a poster at `posters/feastables-motion-ad.jpg`.
2. In `index.html`, find the comment `Project 4`. In that card change `src`, `poster`, `data-title`, the `aria-label`, the title, the type line and the description.

**Poster tip:** export any frame from your video as a JPG, 9:16 shape (for example 720 x 1280), under 150 KB.

**Video tips:** vertical 9:16 MP4 (H.264 + AAC). Keep each file under about 20 MB so the site loads fast and fits free hosting limits. To shrink a file with [FFmpeg](https://ffmpeg.org):

```
ffmpeg -i input.mp4 -vf "scale=720:-2,fps=30" -c:v libx264 -crf 24 -preset slow -movflags +faststart -c:a aac -b:a 96k output.mp4
```

If a video file is missing, the card shows "Video not found" with the path it expected, so you can spot mistakes quickly.

## 3. Edit text, prices and contact details

Everything is in `index.html` as plain text.

- **Prices:** search for `id="pricing"`. Edit the text inside each `price-row`. Copy or delete a whole `<li class="price-row">` to add or remove a line.
- **WhatsApp number:** search and replace `919768536314` (appears in several links) and `+91 9768536314` (the visible number in the contact section).
- **WhatsApp message:** the text after `?text=` in the contact button is URL-encoded. Use any "URL encode" tool to change it.
- **Instagram:** search and replace `convertive.ugc`.
- **Colours and fonts:** the first lines of `assets/styles.css` (`:root`).
- The footer year updates automatically.

## 4. Publish for free

Any of these work. Free-plan limits change, so check the host's pricing page if you add many more videos.

**Netlify Drop (quickest)**
1. Go to `app.netlify.com/drop` and sign in.
2. Drag the whole `convertive-ugc` folder onto the page.
3. You get a live link in about a minute. You can rename it in Site settings.

**Cloudflare Pages**
1. Cloudflare dashboard, Workers & Pages, Create, Pages, Upload assets.
2. Upload the folder. Note that Cloudflare Pages has a per-file size limit (25 MB at the time of writing); your videos are well under it.

**GitHub Pages**
1. Create a GitHub repository and upload the folder contents (`index.html` must be at the top level).
2. Settings, Pages, deploy from the `main` branch.

**Custom domain:** buy a domain (for example convertiveugc.in) from any registrar, then add it in your host's Domains settings and follow the DNS steps shown.

## 5. Social preview (do this after publishing)

When someone shares your link on WhatsApp or Instagram, the preview image comes from `assets/og-image.jpg`. Social apps need the full web address for it:

1. Open `index.html` and find `https://YOUR-DOMAIN.com/assets/og-image.jpg` near the top.
2. Replace `YOUR-DOMAIN.com` with your real address (for example `your-site.netlify.app`).
3. Re-upload `index.html`.

Until you do this, links still work. They just won't show the preview image.

## 6. Check before you share

- Tap each video on your phone. Only one plays at a time, and it pauses when you scroll away.
- Tap "Get Your Ad" and "Start a WhatsApp Conversation". WhatsApp should open a chat with +91 9768536314.
- Tap the Instagram button and confirm it opens @convertive.ugc.
