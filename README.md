# Ringwatch Citadel / Atlas Galactic

Three-page static site, ready for GitHub Pages. No build step or package installation.

## Publish

Upload **the contents of this folder** into the root of your GitHub repository: `index.html`, `active.html`, `planned.html`, `assets/`, `data/`, and `.nojekyll`. In the repository's Pages settings, choose your branch and `/ (root)`. Relative links work on both project Pages URLs and custom domains.

## Update the construction board

Edit `data/colony.json` in GitHub, then commit. GitHub Pages must finish deploying the change before visitors can see it. The site reads the published file on load, every 60 seconds while visible, and when **Refresh manifest** is clicked. This is a commander-maintained board, not an automatic game/Inara feed.

- `updatedAt`: date of the latest commander update, e.g. `2026-10-08`.
- `squadron.url`: currently `null`. Replace with the full HTTPS Inara squadron URL once created; the homepage then displays the squadron link.
- `active`: only projects actually under construction.
- `completed`: operational facilities.
- `planned`: proposed facilities and scouting priorities. These are suggestions, not confirmed orders.
- `cargoCapacity`: Panther cargo capacity used for minimum-load estimates.

Example entry to add **inside the `active` array** (these illustrative numbers are not a real construction manifest):

```json
{
  "id": "unique-project-id",
  "name": "Your installation name",
  "type": "Your selected facility type",
  "location": "System / body / site",
  "status": "Under construction",
  "notes": "Delivery or supply instructions",
  "resources": [
    {"commodity": "Steel", "required": 100, "delivered": 25},
    {"commodity": "Titanium", "required": 50, "delivered": 0}
  ]
}
```

Replace all sample values with the in-game construction manifest. `delivered` is the cumulative amount turned in, not cargo bought. The board calculates remaining demand, project progress, combined commodity totals, and minimum Panther loads. Quantities must be nonnegative numbers. An empty resources array shows “requirements awaiting an in-game construction manifest.”

When construction finishes, remove the active entry and add the facility to `completed`. Keep valid JSON: double quotes, commas between entries, no trailing commas or comments.

## Local preview

Serve this directory with a local HTTP server; opening the HTML directly with `file://` will prevent the JSON request in most browsers. Example with Node or Python tooling already available on your computer. No dependencies are needed by the deployed site.

## Design & data

Dark orange/copper styling, responsive layouts, keyboard navigation and reduced-motion support. Orbital artwork is original CSS/SVG. Google Fonts are optional; local fallback fonts are included. No analytics or tracking scripts.

Current confirmed information was supplied by the commander: Dodec starport, industrial economy, copper/grey livery, and 36 shipyard ships at establishment. Ring types and landable body count were checked through [Inara](https://inara.cz/elite/starsystem/2495269/). Shipyard stock is a historical establishment figure, not a live inventory.

Planning proposals require an in-game survey for placement, dependencies, points and economy outcomes. A refinery facility plus an accessible port is a planning direction, not a promise of a particular commodity output. See [Frontier's Dodec update](https://store.steampowered.com/news/posts/?appids=359320&enddate=1763037221&feed=steam_community_announcements) for refinery-contact restrictions.

Unofficial fan project. Elite Dangerous belongs to Frontier Developments.
