<p align="center">
  <img src="static/logo.png" alt="Trelay" width="80" />
</p>

<h1 align="center">Trelay</h1>

<p align="center"><strong>Your Links, Your Server.</strong></p>

Trelay is a developer-first, privacy-respecting URL shortener and link manager designed for self-hosting. All data stays on your server with no external dependencies or telemetry.

## Why Trelay?

- **Self-hosted**: Your data never leaves your infrastructure
- **Privacy-first**: No tracking, no telemetry, IP anonymization by default
- **Developer-friendly**: Powerful CLI, REST API, and modern dashboard
- **Single container**: Deploy with one Docker command
- **Open source**: MIT licensed, free forever

## Features

- Custom slugs, password protection, expiration dates
- One-time links that self-destruct after first access
- Folder organization, trash with restore
- Click analytics with CSV/JSON export, IP anonymization
- Open Graph preview, QR code generation (download/clipboard)
- Cross-platform CLI with shell completion and table/JSON/CSV output
- REST API with JWT and API key auth; OpenAPI spec in `trelay/api/openapi.yaml`

## Keeping the site in sync

Content and copy are aligned with the **trelay** app. When updating the app (README, features, CLI, API), update this marketing site accordingly: `Hero.svelte`, `Features.svelte`, `CliShowcase.svelte`, `Cta.svelte`, and this README.

## Quick Start (from main repo)

```bash
git clone https://github.com/trelay-dev/trelay.git && cd trelay
cp env.example .env   # set API_KEY, JWT_SECRET
docker compose up -d
# Dashboard at http://localhost:8080
```

## Links

- **Repository**: [github.com/trelay-dev/trelay](https://github.com/trelay-dev/trelay)
- **Documentation**: [github.com/trelay-dev/trelay#readme](https://github.com/trelay-dev/trelay#readme)

## License

MIT
