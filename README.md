# Blangah Bites

A manga-styled food directory of hawker centres and dining spots within 2.5 km of 59 Telok Blangah Heights, Singapore. Pure static HTML/CSS/JS — no build step, no framework, no dependencies.

## What it does

- Lists 11 real hawker centres and dining spots near the home address, each with a live distance calculated in-browser (Haversine formula) from 59 Telok Blangah Heights.
- **Map** button opens Google Maps walking directions from home to that spot.
- **Ratings** button expands a placeholder panel with a link to check current Google reviews (no live ratings API is wired in).
- **GrabFood** / **foodpanda** buttons open a search for that spot on each delivery platform.
- **Budget filter** ($ / $$ / $$$) filters the grid live.
- Anime/manga visual theme, with full light and dark mode support.

## Deploy on Vercel via GitHub

1. Create a new GitHub repository and push this folder to it:

   ```bash
   cd blangah-bites-app
   git init
   git add .
   git commit -m "Initial commit: Blangah Bites food directory"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo>.git
   git push -u origin main
   ```

2. Go to [vercel.com/new](https://vercel.com/new) and import the GitHub repository.
3. Vercel will auto-detect it as a static site (no framework, no build command needed). Leave the settings as-is and click **Deploy**.
4. Your app will be live at `https://<your-project>.vercel.app` within a minute.

Every future push to `main` will auto-deploy.

## Local preview

Just open `index.html` in a browser, or serve it locally:

```bash
npx serve .
```

## Updating the data

The list of places lives in a `PLACES` array near the bottom of `index.html`, inside the `<script>` tag. Each entry has a `name`, `address`, `lat`/`lng`, `category` (`hawker` or `mall`), `budget` (`1`, `2`, or `3`), `cuisines`, and a short `blurb`. Distance is computed automatically from the `HOME` coordinates at the top of the script — edit `HOME` if you ever move.
