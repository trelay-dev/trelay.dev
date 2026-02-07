<script lang="ts">
	import DocPage from '$lib/components/docs/DocPage.svelte';
</script>

<svelte:head>
	<title>Configuration — Trelay Docs</title>
	<meta name="description" content="Trelay environment variables and configuration options." />
</svelte:head>

<DocPage title="Configuration">
	<p class="lead">
		Trelay is configured via environment variables. Use a <code>.env</code> file in the project root (or set variables in your shell or Docker). The app loads <code>.env</code> automatically when present.
	</p>

	<h2>Required variables</h2>
	<table>
		<thead>
			<tr>
				<th>Variable</th>
				<th>Description</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td><code>API_KEY</code></td>
				<td>Secret used to authenticate API requests and dashboard login. Use a long random string (e.g. <code>openssl rand -hex 32</code>).</td>
			</tr>
			<tr>
				<td><code>JWT_SECRET</code></td>
				<td>Secret used to sign JWT tokens. Use a long random string. Keep it private.</td>
			</tr>
		</tbody>
	</table>

	<h2>Server</h2>
	<table>
		<thead>
			<tr>
				<th>Variable</th>
				<th>Description</th>
				<th>Default</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td><code>SERVER_HOST</code></td>
				<td>Bind address</td>
				<td><code>0.0.0.0</code></td>
			</tr>
			<tr>
				<td><code>SERVER_PORT</code></td>
				<td>HTTP port</td>
				<td><code>8080</code></td>
			</tr>
			<tr>
				<td><code>SERVER_READ_TIMEOUT</code></td>
				<td>Read timeout (e.g. <code>10s</code>)</td>
				<td><code>10s</code></td>
			</tr>
			<tr>
				<td><code>SERVER_WRITE_TIMEOUT</code></td>
				<td>Write timeout (e.g. <code>30s</code>)</td>
				<td><code>30s</code></td>
			</tr>
			<tr>
				<td><code>SERVER_SHUTDOWN_TIMEOUT</code></td>
				<td>Graceful shutdown timeout</td>
				<td><code>10s</code></td>
			</tr>
		</tbody>
	</table>

	<h2>Database</h2>
	<table>
		<thead>
			<tr>
				<th>Variable</th>
				<th>Description</th>
				<th>Default</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td><code>DB_DRIVER</code></td>
				<td><code>sqlite3</code> or <code>postgres</code></td>
				<td><code>sqlite3</code></td>
			</tr>
			<tr>
				<td><code>DB_PATH</code></td>
				<td>SQLite database file path (used when <code>DB_DRIVER=sqlite3</code>)</td>
				<td><code>trelay.db</code></td>
			</tr>
			<tr>
				<td><code>DB_URL</code></td>
				<td>PostgreSQL connection string (when <code>DB_DRIVER=postgres</code>)</td>
				<td>—</td>
			</tr>
			<tr>
				<td><code>DB_MAX_CONNS</code></td>
				<td>Max DB connections (Postgres)</td>
				<td><code>10</code></td>
			</tr>
		</tbody>
	</table>

	<h2>Authentication</h2>
	<table>
		<thead>
			<tr>
				<th>Variable</th>
				<th>Description</th>
				<th>Default</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td><code>TOKEN_EXPIRY</code></td>
				<td>JWT token lifetime (e.g. <code>24h</code>)</td>
				<td><code>24h</code></td>
			</tr>
		</tbody>
	</table>

	<h2>Application</h2>
	<table>
		<thead>
			<tr>
				<th>Variable</th>
				<th>Description</th>
				<th>Default</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td><code>BASE_URL</code></td>
				<td>Public URL for short links (e.g. <code>https://links.example.com</code>)</td>
				<td><code>http://localhost:8080</code></td>
			</tr>
			<tr>
				<td><code>DEFAULT_DOMAIN</code></td>
				<td>Default domain for new links (optional)</td>
				<td>—</td>
			</tr>
			<tr>
				<td><code>CUSTOM_DOMAINS</code></td>
				<td>Comma-separated list of allowed custom domains</td>
				<td>—</td>
			</tr>
			<tr>
				<td><code>STATIC_DIR</code></td>
				<td>Path to frontend build output (serve SPA from server)</td>
				<td>—</td>
			</tr>
			<tr>
				<td><code>ANALYTICS_ENABLED</code></td>
				<td>Enable click tracking</td>
				<td><code>true</code></td>
			</tr>
			<tr>
				<td><code>IP_ANONYMIZATION</code></td>
				<td>Anonymize IP addresses in analytics</td>
				<td><code>true</code></td>
			</tr>
			<tr>
				<td><code>SLUG_LENGTH</code></td>
				<td>Default length for auto-generated slugs (4–32)</td>
				<td><code>6</code></td>
			</tr>
			<tr>
				<td><code>MAX_URL_LENGTH</code></td>
				<td>Maximum length of original URLs</td>
				<td><code>2048</code></td>
			</tr>
			<tr>
				<td><code>RATE_LIMIT_PER_MIN</code></td>
				<td>API rate limit (requests per minute per client)</td>
				<td><code>100</code></td>
			</tr>
		</tbody>
	</table>

	<h2>Example .env</h2>
	<pre class="code-block"><code># Required
API_KEY=your_secure_api_key_here
JWT_SECRET=your_secure_jwt_secret_here

# Server
SERVER_PORT=8080

# Database (SQLite)
DB_DRIVER=sqlite3
DB_PATH=trelay.db

# Public URL for short links
BASE_URL=https://links.example.com

# Optional
ANALYTICS_ENABLED=true
IP_ANONYMIZATION=true
RATE_LIMIT_PER_MIN=100</code></pre>
</DocPage>
