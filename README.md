# Studio T Creative · Paid Ads Landing Page

The destination for all paid ad traffic. Separate from the portfolio site so the two can be
deployed, edited and measured independently.

## What is in here

```
index.html          the entire page, all CSS and JS inline
assets/opt/         55 files: 50 images and 5 reels
vercel.json         clean URLs and a one year cache on the media
.gitignore          only assets/opt ships, everything else stays out
```

No build step, no dependencies, no framework. It is static files. Total size is about 17MB.

> **Do not copy the whole `assets/` folder in here.** Only `assets/opt/` belongs in this repo.
> The raw source folders (`Videos`, `photos`, `poke`, `stories`, `font`) are roughly 380MB of
> full resolution originals. `.gitignore` is set to ignore everything under `assets/` except
> `opt`, so a stray copy will not be committed, but it will still bloat your local folder.

## Deploying to Vercel

1. Push this folder to its own GitHub repo.
2. In Vercel, "Add New Project" and import that repo.
3. Framework Preset: **Other**. Leave Build Command and Output Directory blank.
4. Deploy.

After it goes live, open the URL on a phone and confirm the images load and one reel plays.
Anything blank means a file is missing from `assets/opt/`, not a problem with the page.

## Where the leads go

- Primary CTA, "Take Next Step", every instance points to the HoneyBook form:
  `https://studiotcreative.hbportal.co/public/68a789aac5ac6c002ff015ce`
- Secondary path is the Calendly 15 minute strategy call:
  `https://calendly.com/hello-studiot-creative/15min`
  It is embedded as an inline widget in the booking section and loads only when a visitor
  scrolls near it, so it does not slow the page down on mobile data.

To change either destination, find and replace the URL in `index.html`.

## Notes for editing

- **Colors are fixed to the brand:** Crema `#FAF0E3`, Mauve `#C4897A`, Terracota `#7A3520`,
  dark ink `#2b1710` for depth. Coral `#FF5A36` is a highlight only. It appears on primary
  CTAs, the most popular package flag, the three results numbers and the small hero dots.
  Do not spread it further or it stops reading as a highlight.
- **Fonts:** Playfair Display for headings, Montserrat for body, Great Vibes for the script
  accent. Loaded from Google Fonts.
- **Copy rules:** no em dashes or en dashes anywhere, use commas, periods or middots. Never
  state prices, use "scoped after a discovery call".
- **Videos** use `preload="none"` with poster images so the page stays fast on mobile data.
  If you add a reel, add a matching poster JPG or the tile will be a blank box until it plays.
- The `assets/opt/` folder is a copy. The portfolio repo has its own copy of the same media.
  If you re-export an image, update it in both places.

## Page structure

Hero · client strip · five services · results and the before/after feed · proof
(five reels plus a tabbed gallery) · the studio team · three packages · Calendly
booking · closing CTA · footer.

## Media in this folder

Reels: American Mane (3), Busy Bod (2).

Gallery tabs and what is in each:

| Tab | Count | Content |
|---|---|---|
| Food & Hospitality | 18 | Poke Company, restaurant and cafe photography, beverage, bakery |
| Medical | 5 | American Mane consultation, procedure, clinical detail, results |
| Wellness | 4 | Busy Bod stills and campaign graphics |
| Retail & Product | 8 | Weber Grill, candle and packaging product work |
| Brand & Web | 8 | Website design, design system, content mockups, seasonal, Spanish work |

Team photos are `team_group`, `team_meeting`, `team_duo` and `team_phones`.
The before/after feed comparison is `feed_evolution_phones.jpg`.

Naming convention: `team_*` studio team, `work_*` client work without a brand prefix,
`muddy_*` cafe and hospitality, and the rest are prefixed by client (`poke_`, `mane_`,
`weber_`, `reel_`, `story_`).
