<p align="center">
  <img src="static/logo.png" alt="Trelay" width="80" />
</p>

<h1 align="center">Trelay</h1>

<p align="center"><strong>Your Links, Your Server.</strong></p>

This repo is the marketing site and docs for **Trelay**, the self-hosted URL manager. The app itself lives at [github.com/trelay-dev/trelay](https://github.com/trelay-dev/trelay).

What you see on the public web as **v2.0** is the open source stack (Go + SvelteKit). Older iterations were never open sourced, which is why you will not find a v1 release on GitHub.

## Why Trelay?

- **Self-hosted**: data stays on your box
- **Privacy-minded**: no vendor analytics in the product; IP anonymization by default
- **Built for operators**: CLI, HTTP API, and a real dashboard
- **One container** to run in production
- **MIT license**

## Features (high level)

- Custom slugs, passwords, expiry, one-time links
- Folders, trash, restore
- Click stats with CSV/JSON export
- Open Graph previews, QR codes
- CLI with completion; REST API and OpenAPI spec in the main repo

## Quick start (clone the app)

```bash
git clone https://github.com/trelay-dev/trelay.git && cd trelay
cp env.example .env   # set API_KEY, JWT_SECRET
docker compose up -d
# Dashboard: http://localhost:8080
```

## Links

- **App source**: [github.com/trelay-dev/trelay](https://github.com/trelay-dev/trelay)
- **README / setup**: [github.com/trelay-dev/trelay#readme](https://github.com/trelay-dev/trelay#readme)

## License

MIT
