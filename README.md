# rpcdesk website

Static marketing site for [rpcdesk](https://github.com/RPCDesk/rpcdesk), served from
Cloudflare Pages.

- **Production:** https://rpcdesk.ayushb.com (also https://rpcdesk.pages.dev)
- **Pages project:** `rpcdesk`
- **Build step:** none — plain HTML and CSS

## Editing

Everything lives at the repository root: `index.html`, `styles.css`, and `assets/`.
There is no bundler, no framework, and no dependencies; open `index.html` directly or run
`python3 -m http.server` to preview.

Screenshots in `assets/` are captured from the running macOS app (Settings → Appearance,
then `screencapture -l <window id>`), cropped to the window, and exported as JPEG at
1200–1800 px wide. The palette shown in each tile must match the theme name.

## Deploying

Pushes to `main` deploy automatically through `.github/workflows/deploy.yml`, which runs
`wrangler pages deploy`. It needs two repository secrets:

| Secret | Purpose |
| --- | --- |
| `CLOUDFLARE_API_TOKEN` | Token with **Cloudflare Pages: Edit** |
| `CLOUDFLARE_ACCOUNT_ID` | Account that owns the `rpcdesk` project |

To deploy by hand:

```sh
CLOUDFLARE_API_TOKEN=... bunx wrangler@4 pages deploy . --project-name rpcdesk --branch main
```

The custom domain is attached to the Pages project, so no DNS change is needed per deploy.

## Licensing

MIT — see [LICENSE](LICENSE). The app itself lives in
[RPCDesk/rpcdesk](https://github.com/RPCDesk/rpcdesk).
