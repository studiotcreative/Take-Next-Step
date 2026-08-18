# Studio T Creative · Paid Ads Landing Page

The destination for all paid ad traffic. Separate from the portfolio site so the two can be
deployed, edited and measured independently.

Live at **take-next-step.vercel.app** · repo `studiotcreative/Take-Next-Step`

## What is in here

```
index.html          the entire page, all CSS and JS inline
vercel.json         clean URLs and a one year cache on the media
.gitignore          blocks every raw source format
assets/
  american-mane/    medical, 3 reels + posters + 5 stills
  busy-bod/         wellness, 3 reels + posters + 2 product stills
  candy-cream/      dessert, 2 reels + posters + 14 graphics and textures
  feed/             the before and after Instagram comparison
  food-cocktail/    restaurant and beverage photography
  happy-fish/       restaurant plating
  moody-root/       coffee shop and hospitality
  poke-company/     10 stills and carousels
  product/          candle and packaging product work
  stories/          55 Studio T social designs, EN and ES
  studio-t/         the team photos
```

No build step, no dependencies, no framework. About 29MB, 127 files.

## Deploying

Push to GitHub and Vercel rebuilds on its own, usually within a minute. Editing files on the
Mac does nothing until they reach GitHub. If you are importing fresh: Framework Preset
**Other**, Build Command and Output Directory both blank.

## Rules that keep this from breaking

**Only optimized media ships.** `.jpg` and lowercase `.mp4` are the only formats that belong
under `assets/`. `.png`, `.mov`, `.MP4`, `.otf`, `.zip` and friends are blocked by
`.gitignore`, because dropping a raw source folder in here has already ballooned the repo
twice, once to 397MB and once to 273MB.

To add media, optimize it first. ImageMagick and ffmpeg are both installed on the Mac:

```
# image
convert SRC -auto-orient -resize '1400x1400>' -strip -interlace Plane -quality 80 assets/CLIENT/name.jpg

# vertical reel
ffmpeg -i SRC -vf "scale='min(720,iw)':-2" -c:v libx264 -preset veryfast -crf 30 \
  -pix_fmt yuv420p -movflags +faststart -c:a aac -b:a 96k assets/CLIENT/reel_name.mp4

# poster for that reel, required or the tile is a blank box
ffmpeg -ss 0.5 -i assets/CLIENT/reel_name.mp4 -frames:v 1 -vf scale=720:-2 -q:v 4 \
  assets/CLIENT/reel_name_poster.jpg
```

**No spaces, ampersands, apostrophes or uppercase in file or folder names.** macOS tolerates
them, web URLs do not, and `&` in particular breaks a path outright. Use lowercase with
hyphens.

**macOS is case insensitive, Vercel's Linux servers are not.** `Photo.JPG` and `photo.jpg`
are the same file locally and different files in production. Case-check before pushing.

## Where the leads go

- Primary CTA, "Take Next Step", ten instances, all pointing at the HoneyBook form:
  `https://studiotcreative.hbportal.co/public/68a789aac5ac6c002ff015ce`
- Secondary path is the Calendly 15 minute strategy call:
  `https://calendly.com/hello-studiot-creative/15min`
  Embedded as an inline widget that loads only when a visitor scrolls near it.

To change either, find and replace the URL in `index.html`.

## Page structure

Hero · five services · results with the before and after feed · proof, being 8 reels plus a
five tab gallery · the studio team · three packages · Calendly booking · closing CTA · footer.

| Gallery tab | Count | Content |
|---|---|---|
| Food & Drink | 16 | Poke Company, Happy Fish, restaurant and beverage photography |
| Dessert & Café | 13 | Candy Cream campaigns and textures, Moody Root coffee |
| Medical | 5 | American Mane consultation, procedure, clinical detail, results |
| Wellness & Product | 7 | Busy Bod, candle and packaging product work |
| Brand & Web | 10 | Brand identity, website design, design system, EN and ES content |

Reels, 8 total: American Mane 3, Busy Bod 3, Candy Cream 2.

## Design rules

- **Palette is fixed.** Crema `#FAF0E3`, Mauve `#C4897A`, Terracota `#7A3520`, dark ink
  `#2b1710` for depth. Coral `#FF5A36` is a highlight only, appearing on primary CTAs, the
  most popular package flag, the three results numbers and the small bullet dots. Spreading
  it further stops it reading as a highlight.
- **Fonts:** Playfair Display headings, Montserrat body, Great Vibes script accent.
- **Copy:** no em dashes or en dashes anywhere, use commas, periods or middots. Never state
  prices, use "scoped after a discovery call".
- Videos use `preload="none"` with poster images so the page stays fast on mobile data.

## Notes

`assets/stories/` holds all 55 optimized Studio T social designs but the page only uses 10 of
them. The rest are kept as a ready pool for swapping the Brand & Web tab without re-exporting
anything. Same for `studio-t/team_celebrate.jpg`, which is optimized but unused.
