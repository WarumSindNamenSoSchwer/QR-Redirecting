# QR-Redirecting

> Static QR codes that behave like dynamic ones — free, no third-party service.

## Why

Dynamic QR-code providers charge €3–10/month per code so you can update the
destination URL without reprinting. For a stack of business cards that felt
absurd, so I built the same thing in two HTML files and GitHub Pages.

## How it works

1. Each QR code on the card points to a stable URL on **GitHub Pages**, e.g.
   `https://warumsindnamensoschwer.github.io/QR-Redirecting/link1.html`.
2. That page contains a `<meta http-equiv="refresh">` plus a JS `window.location`
   fallback — visitors are redirected within ~0 ms.
3. To change the destination later, edit the `URL=` value in the HTML file,
   push the commit. New scans hit the new target. The printed QR never changes.

```html
<meta http-equiv="refresh" content="0; URL='https://your-target.example/'" />
<script>window.location.href = "https://your-target.example/";</script>
```

## Layout

| File | Purpose |
|------|---------|
| `link1.html` | QR slot 1 — points wherever you set the `URL='…'` |
| `link2.html` | QR slot 2 — independent target |

Add `link3.html`, `link4.html`, … for more independent QR codes.

The two files in this repo are deployed live and forward to a former client's
sites — the printed cards are still in circulation, so the redirects stay up.
Treat the file contents as a working example, not as fixed config.

## Setup (replicate for your own cards)

1. Fork this repo.
2. Settings → Pages → deploy from `main` branch, `/` root.
3. Edit the `URL='...'` in each HTML file to your initial target.
4. Generate the QR codes pointing at the Pages URLs (any free QR generator).
5. Print, hand out, profit. Edit the HTML whenever the target moves.

## Caveats

- GitHub Pages has no SLA — fine for business cards, not for high-traffic links.
- No click analytics. Wrap the redirect in a UTM-tagged URL if you need them.
- Repository must stay public for free Pages hosting.

## License

- **Code** (HTML files) — [MIT](LICENSE)
- **Documentation** (this README) — [CC BY-NC 4.0](LICENSE-DOCS)

Copy the code freely, never pay for a dynamic QR service again. Attribution required for both.
