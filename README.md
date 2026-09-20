# LoonNet — standalone site for loonnet.humanitarians.ai

Static site: four Godot web exports (~190 MB, threads disabled so no cross-origin-isolation headers are needed),
a landing page, the proposal page, and screenshots. No build step, no framework.

## Layout
- `index.html`            landing page (game grid + in-page player); `#nest-site` etc. deep-link into the player
- `nest-site/ deep-dive/ runway/ chick-taxi/`   the games, same paths as the GitHub Pages copy
- `project/index.html`    the proposal page (game links rewritten to relative)
- `screenshots/`, `loonnet-hero.jpg`
- `vercel.json`           long cache on .wasm/.pck

## Deploy
1. New GitHub repo (e.g. `nikbearbrown/loonnet`), copy this folder in, push.
2. Vercel → New Project → import the repo → Framework preset **Other**, no build command, output `.` → Deploy.
3. Project → Settings → Domains → add `loonnet.humanitarians.ai`.
4. GoDaddy DNS for humanitarians.ai → add record:  `CNAME  loonnet  →  cname.vercel-dns.com`
   (same pattern as `madison.humanitarians.ai`).
5. Once it resolves, merge the `remove-loonnet` branch on humanitarians_html so `/loonnet/*` on the main site
   301s to the subdomain.

## URL map (old → new)
- humanitarians.ai/loonnet                          → loonnet.humanitarians.ai
- humanitarians.ai/loonnet/project/index.html       → loonnet.humanitarians.ai/project/index.html
- sheshngupta.github.io/loonnet-games/<game>/index.html → loonnet.humanitarians.ai/<game>/index.html
