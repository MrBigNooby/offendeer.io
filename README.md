# offendeer.com

Portfolio site for offendeer, a Roblox developer. It's one self-contained page: no build step, no dependencies, and fonts load from Google Fonts.

## Files

| File | What it does |
| --- | --- |
| `index.html` | The whole site: markup, styles, ASCII art engine and Discord card |
| `404.html` | Page GitHub Pages shows for any broken link |
| `CNAME` | Tells GitHub Pages to serve the site at `offendeer.com` |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is instead of running Jekyll |

## Put it on GitHub Pages

1. Create a new **public** repository on GitHub, for example `offendeer.com`.
2. Upload all four files to the root of the repository (**Add file → Upload files**, then commit).
   If the uploader skips `.nojekyll`, the site still works without it.
3. Open **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*, pick `main` and `/ (root)`, and save.
4. In the same page, the **Custom domain** box should already say `offendeer.com` (it reads the `CNAME` file). If not, type it in and save.

## Point offendeer.com at GitHub

At the company where you bought the domain, open its DNS settings and add these records.

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

**CNAME record** (host `www`): `YOUR-GITHUB-USERNAME.github.io`

Remove any other A, AAAA or CNAME records for `@` and `www`, such as a parking page.

DNS can take anywhere from a few minutes to a day. Once GitHub shows the domain as verified in **Settings → Pages**, tick **Enforce HTTPS**.

## Editing the site

Everything is in `index.html`. Edit it on GitHub (the pencil icon), commit, and the site updates in a minute or two.

- **Discord**: `DISCORD_ID` near the top of the `<script>` sets the profile every Contact button opens. The card's picture, name, status and banner update on their own through Lanyard, which needs you to stay in the Lanyard Discord server (discord.gg/lanyard).
- **Adding work**: copy an `<article class="proj">` block in the Selected Work section. Set `data-cat` to one or more of `scripting ui building animation modeling vfx`, and a filter button appears for each one in use. For a picture, upload the image next to `index.html` and use `<canvas class="ascii" data-img="your-image.png"></canvas>`; it is turned into ASCII art when the page loads.
- **Motion**: every animation runs for every visitor, including people whose system asks for reduced motion. Set `CALM` to `true` near the top of the script to drop the large movements for them.
