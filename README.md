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
- Tags and folder organization
- Analytics with CSV/JSON export
- QR code generation
- Full CLI with pipe support and multiple output formats
- RESTful API with JWT and API key authentication

## Quick Start

```bash
docker run -p 8080:8080 trelay/trelay
```

## Links

- **Repository**: [github.com/trelay-dev/trelay](https://github.com/trelay-dev/trelay)
- **Documentation**: [github.com/trelay-dev/trelay#readme](https://github.com/trelay-dev/trelay#readme)

## License

MIT
