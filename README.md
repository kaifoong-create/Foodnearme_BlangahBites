# Blangah Bites

A monster-catching food quest: hawker centres and dining spots within 2.5 km of 59 Telok Blangah Heights, Singapore, each guarded by an original food critter you catch and track in a Food-dex. Pure static HTML/CSS/JS — no build step, no framework, no dependencies.

## What it does

- Lists 11 real hawker centres and dining spots near the home address, each with a live distance calculated in-browser (Haversine formula) from 59 Telok Blangah Heights.
- Every spot has an original, invented food critter (name, sprite, flavor "type") — not any copyrighted franchise's characters or logos.
- **Catch!** button marks a spot as caught; progress is saved to `localStorage` (this browser only, not synced).
- **Food-dex** section shows all 11 critters as a collection grid — caught ones are revealed, undiscovered ones show as "???". Click a dex slot to jump to that card.
- **Map** button opens Google Maps walking directions from home to that spot.
- **Ratings** button expands a placeholder panel with a link to check current Google reviews (no live ratings API is wired in).
- **GrabFood** button opens a pre-filled search on GrabFood's Singapore site; **foodpanda** opens their Singapore city listing. Both require the delivery address to be set in-app before they show what's actually deliverable to that spot.
- **Budget** filter ($ / $$ / $$$) and **Status** filter (All / Caught / Uncaught) filter the grid live, combined.
- Retro monster-catching RPG pixel theme (Press Start 2P + Baloo 2), with full light and dark mode support.

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

The list of places lives in a `PLACES` array near the bottom of `index.html`, inside the `<script>` tag. Each entry has an `id` (stable key used for catch-state storage — don't change this once someone has caught it), `name`, `address`, `lat`/`lng`, `category` (`hawker` or `mall`), `budget` (`1`, `2`, or `3`), `cuisines`, a short `blurb`, and `creature`/`sprite`/`type` (`ember`, `aqua`, `leaf`, or `spark`) for the Food-dex entry. Distance is computed automatically from the `HOME` coordinates at the top of the script — edit `HOME` if you ever move.
