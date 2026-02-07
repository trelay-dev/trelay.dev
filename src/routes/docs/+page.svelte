<script lang="ts">
	import DocPage from '$lib/components/docs/DocPage.svelte';
</script>

<svelte:head>
	<title>Documentation — Trelay</title>
	<meta name="description" content="Trelay documentation: getting started, installation, configuration, CLI, and API." />
</svelte:head>

<DocPage title="Overview">
	<p class="lead">
		Trelay is a developer-first, privacy-respecting URL manager for self-hosting. Run it on your own server and keep full control of your links, analytics, and data.
	</p>

	<h2>What is Trelay?</h2>
	<p>
		Trelay shortens URLs, tracks clicks (with optional IP anonymization), organizes links in folders, and supports one-time links, password protection, and expiration. It provides a modern web dashboard, a cross-platform CLI, and a REST API so you can manage links from the terminal, scripts, or other apps.
	</p>

	<h2>Features</h2>
	<ul>
		<li><strong>URL shortening</strong> — Custom slugs, expiration, and password protection</li>
		<li><strong>One-time links</strong> — Links that self-destruct after first access</li>
		<li><strong>Folder management</strong> — Organize links into folders</li>
		<li><strong>Custom domain</strong> — Use <code>BASE_URL</code> so short links use your domain</li>
		<li><strong>Click analytics</strong> — Total clicks, daily stats, top referrers; export to CSV or JSON</li>
		<li><strong>Open Graph preview</strong> — Fetch title, description, and image for any URL</li>
		<li><strong>QR codes</strong> — Generate QR codes with download and clipboard support</li>
		<li><strong>Trash & restore</strong> — Soft-delete links and restore them later</li>
		<li><strong>Cross-platform CLI</strong> — Create, list, stats, QR, folders; shell completion</li>
		<li><strong>REST API</strong> — JWT and API key auth; OpenAPI spec included</li>
		<li><strong>Security</strong> — Rate limiting, secure headers, no telemetry</li>
		<li><strong>Single container</strong> — Docker Compose; SQLite by default</li>
	</ul>

	<h2>Quick start</h2>
	<p>Get Trelay running in a few steps:</p>
	<pre class="code-block"><code>git clone https://github.com/trelay-dev/trelay.git
cd trelay
cp env.example .env
# Edit .env: set API_KEY and JWT_SECRET
docker compose up -d</code></pre>
	<p>Open the dashboard at <code>http://localhost:8080</code>. Next, see <a href="/docs/installation">Installation</a> for detailed setup and <a href="/docs/configuration">Configuration</a> for environment options.</p>

	<h2>Documentation index</h2>
	<ul>
		<li><a href="/docs/installation">Installation</a> — Docker and manual setup (server, frontend, CLI)</li>
		<li><a href="/docs/configuration">Configuration</a> — Environment variables and defaults</li>
		<li><a href="/docs/cli">CLI Reference</a> — Commands, flags, and shell completion</li>
		<li><a href="/docs/api">API Reference</a> — Endpoints, auth, and request/response formats</li>
		<li><a href="/docs/import-export">Import & Export</a> — CSV/JSON import and export</li>
	</ul>
</DocPage>
