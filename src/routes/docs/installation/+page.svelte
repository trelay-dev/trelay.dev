<script lang="ts">
	import DocPage from '$lib/components/docs/DocPage.svelte';
</script>

<svelte:head>
	<title>Installation — Trelay Docs</title>
	<meta name="description" content="Install Trelay with Docker or manual setup: server, frontend, and CLI." />
</svelte:head>

<DocPage title="Installation">
	<p class="lead">
		You can run Trelay with Docker Compose (recommended) or build and run the server, frontend, and CLI manually.
	</p>

	<h2>Docker (recommended)</h2>
	<p>Use Docker Compose for a single-command setup. The image builds the Go server and SvelteKit frontend and serves them from one container.</p>

	<h3>1. Clone and configure</h3>
	<pre class="code-block"><code>git clone https://github.com/trelay-dev/trelay.git
cd trelay
cp env.example .env</code></pre>
	<p>Edit <code>.env</code> and set at least:</p>
	<ul>
		<li><code>API_KEY</code> — A secure random string used to authenticate API and dashboard (e.g. generate with <code>openssl rand -hex 32</code>)</li>
		<li><code>JWT_SECRET</code> — A secure random string for signing JWT tokens (e.g. <code>openssl rand -hex 32</code>)</li>
	</ul>
	<p>Optionally set <code>BASE_URL</code> to your public URL (e.g. <code>https://links.example.com</code>) so short links use that domain.</p>

	<h3>2. Run</h3>
	<pre class="code-block"><code>docker compose up -d</code></pre>
	<p>The app listens on port <code>8080</code>. Open <code>http://localhost:8080</code> for the dashboard. Data is stored in a Docker volume (<code>trelay-data</code>) so it persists across restarts.</p>

	<h2>Manual setup</h2>
	<p>For development or when you prefer not to use Docker:</p>

	<h3>Prerequisites</h3>
	<ul>
		<li>Go 1.21+</li>
		<li>Bun 1.0+ (for the frontend)</li>
		<li>SQLite 3</li>
		<li>Make (optional)</li>
	</ul>

	<h3>Server</h3>
	<pre class="code-block"><code>cp env.example .env
# Edit .env with API_KEY and JWT_SECRET
make build-server
./bin/trelay-server</code></pre>
	<p>The server runs on <code>http://localhost:8080</code> by default. Without a built frontend, it will serve the API only; you can develop the frontend separately.</p>

	<h3>Frontend (development)</h3>
	<pre class="code-block"><code>cd frontend
bun install
bun run dev</code></pre>
	<p>The Vite dev server runs at <code>http://localhost:5173</code> with hot reload. Configure the frontend to use your server URL (e.g. <code>http://localhost:8080</code>) for API calls.</p>

	<h3>Production frontend</h3>
	<p>Build the frontend and point the server at the build output:</p>
	<pre class="code-block"><code>cd frontend
bun run build</code></pre>
	<p>Set <code>STATIC_DIR</code> in <code>.env</code> to the path of the built static files (e.g. <code>frontend/build</code> or the equivalent output directory). The server will serve the SPA from that path.</p>

	<h3>CLI</h3>
	<p>Build the CLI (requires a CLI entrypoint in the repo; if you use the API only, you can skip this):</p>
	<pre class="code-block"><code>make build-cli
./bin/trelay config set api-url http://localhost:8080
./bin/trelay config set api-key YOUR_API_KEY
./bin/trelay create https://example.com --slug my-link
./bin/trelay list</code></pre>
	<p>See <a href="/docs/cli">CLI Reference</a> for all commands.</p>

	<h2>Health check</h2>
	<p>Verify the server is running:</p>
	<pre class="code-block"><code>curl http://localhost:8080/healthz</code></pre>
	<p>Expected response: <code>{'{"status":"ok"}'}</code></p>
</DocPage>
