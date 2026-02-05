# Trelay Website

Marketing website for [Trelay](https://github.com/trelay-dev/trelay) - the developer-first, privacy-respecting URL shortener.

## Tech Stack

- **Framework**: SvelteKit 2.x with Svelte 5
- **Styling**: Custom CSS with design system
- **Package Manager**: Bun

## Development

```bash
# Install dependencies
bun install

# Start development server
bun run dev

# Build for production
bun run build

# Preview production build
bun run preview
```

## Project Structure

```
src/
├── app.css              # Global styles and design system
├── app.html             # HTML template
├── lib/
│   └── components/      # Reusable components
│       ├── Nav.svelte
│       ├── Hero.svelte
│       ├── Features.svelte
│       ├── CliShowcase.svelte
│       ├── Comparison.svelte
│       ├── Cta.svelte
│       └── Footer.svelte
└── routes/
    ├── +layout.svelte   # Root layout
    └── +page.svelte     # Homepage
```

## Features

- Responsive design (mobile, tablet, desktop)
- Light and dark theme support
- Modern, minimal aesthetic
- Accessible navigation
- SEO optimized

## License

MIT
