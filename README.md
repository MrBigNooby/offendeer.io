# offendeer.com

Portfolio site for offendeer, a Roblox developer. It's one self-contained page: no build step, no dependencies, and fonts load from Google Fonts.

Live at **https://mrbignooby.github.io/offendeer.io/** until the custom domain is set up.

## Files

| File | What it does |
| --- | --- |
| `index.html` | The whole site: markup, styles, ASCII art engine and Discord card |
| `404.html` | Page GitHub Pages shows for any broken link |
| `assets/games/` | Each game's icon and thumbnails (WebP). The ASCII art on the site is drawn from these files when the page loads |
| `CNAME` | The custom domain, `offendeer.com` (see the note below) |
| `.github/workflows/static.yml` | Publishes the site to GitHub Pages on every push to `main` |

## How it deploys

Every commit to `main` runs the **Deploy static content to Pages** workflow, and the site updates a minute or two later. You can watch it under the **Actions** tab.

## Moving it to offendeer.com

Because this repo deploys with GitHub Actions, GitHub ignores the `CNAME` file. The domain has to be set in the repo settings, and the domain's DNS has to point at GitHub first.

1. At the company where you bought the domain, open its DNS settings and add these records.

   **A records** (host `@`):

   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

   **AAAA records** (host `@`, optional but recommended):

   ```
   2606:50c0:8000::153
   2606:50c0:8001::153
   2606:50c0:8002::153
   2606:50c0:8003::153
   ```

   **CNAME record** (host `www`): `mrbignooby.github.io`

   Remove any other A, AAAA or CNAME records for `@` and `www`, such as a parking page.

2. Go to **Settings → Pages → Custom domain**, type `offendeer.com` and save. Do this after the DNS records exist; once a custom domain is set, the github.io address redirects to it.
3. DNS can take anywhere from a few minutes to a day. Once GitHub shows the domain as verified, tick **Enforce HTTPS**.

## Editing the site

Everything is in `index.html`. Edit it on GitHub (the pencil icon) and commit; the workflow publishes the change.

- **Discord**: `DISCORD_ID` near the top of the `<script>` sets the profile every Contact button opens. The card's picture, name, status and banner update on their own through Lanyard, which needs you to stay in the Lanyard Discord server (discord.gg/lanyard).
- **Adding work**: copy an `<article class="proj">` block in the Selected Work section. Set `data-cat` to one or more of `scripting ui building animation modeling vfx`, and a filter button appears for each one in use. For a picture, upload the image next to `index.html` and use `<canvas class="ascii" data-img="your-image.png"></canvas>`; it is turned into ASCII art when the page loads.
- **Images**: to change a game's icon or thumbnail, upload a new image to `assets/games/` with the same file name (for example `kombinat-2.webp`). The ASCII art and the gallery both update. PNG or JPG works too if you also change the file name in `index.html`.
- **Project pages**: each project has its own page, an `<article class="pview" id="project-...">` block after `</main>`, opened at `offendeer.com/#project-...`. To add one, copy a block, give it a new `id` and `data-title`, and point the project card's links at `#project-<new id>`. The overview, "What I built" and "What's next" text is placeholder copy, so rewrite it freely.
- **Motion**: every animation runs for every visitor, including people whose system asks for reduced motion. Set `CALM` to `true` near the top of the script to drop the large movements for them.
