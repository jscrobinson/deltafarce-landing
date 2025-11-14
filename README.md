# Delta Farce Landing Page

Landing page for deltafarce.win domain with ads.txt configuration.

## Features

- Simple, responsive landing page
- Links to subdomains (HOTAS configurator, Walking Simulator, etc.)
- ads.txt for Google AdSense verification
- Community links (Discord, GitHub)

## Deployment

Deploy to Cloudflare Pages:

```bash
wrangler pages deploy . --project-name=deltafarce-landing --branch=main
```

## Structure

```
├── index.html    # Main landing page
├── ads.txt       # Google AdSense verification
└── wrangler.toml # Cloudflare Pages config
```

## ads.txt

The ads.txt file is served at the root domain (deltafarce.win/ads.txt) and applies to all subdomains per IAB standards.
