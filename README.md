# Now.gg wrapper (GitHub Pages)

This repository contains a static `index.html` intended for GitHub Pages. It provides:
- A one-click button to open the target site in a new tab.
- A popup-button variant.
- An iframe attempt to embed the site (likely blocked by the remote site).

## Important notes
- **GitHub Pages is static**: you cannot run a server-side proxy here. Many sites (including now.gg) send headers like `X-Frame-Options: DENY` or CSP rules that prevent being embedded in an iframe. That is enforced by browsers for security and cannot be bypassed from static hosting.
- The `iframe` in `index.html` is a best-effort attempt but will usually appear blank or fail if the remote site blocks framing.

## If you *must* embed the site for development/testing
You need a server-side proxy or a local dev trick (for local-only testing). Example options:
- **Local proxy** (Node.js + `http-proxy-middleware`) that strips framing headers and rewrites absolute URLs. This must run on a server you control (not GitHub Pages). See earlier-provided `proxy.js` example.
- **Browser extension** like Requestly / Modify Header (for local testing) to remove `X-Frame-Options`/CSP. Use only for local dev.
- **Puppeteer / headless browser** if you only need screenshots or automated testing (not embedding in a page).

## Legal & ethical
Do not use proxies or header-removal to impersonate, phish, or violate terms of service. Use these techniques only for legitimate development and testing with sites you own or have permission to proxy.

