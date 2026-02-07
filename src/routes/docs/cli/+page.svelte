<script lang="ts">
	import DocPage from '$lib/components/docs/DocPage.svelte';
</script>

<svelte:head>
	<title>CLI Reference — Trelay Docs</title>
	<meta name="description" content="Trelay CLI commands: create, list, get, delete, stats, qr, folder, config, completion." />
</svelte:head>

<DocPage title="CLI Reference">
	<p class="lead">
		The Trelay CLI lets you create links, list them, view stats, generate QR codes, manage folders, and configure the client from the terminal. It supports multiple output formats (table, JSON, CSV) and shell completion.
	</p>

	<h2>Setup</h2>
	<p>Build the CLI (from the trelay repo) and configure the API URL and API key:</p>
	<pre class="code-block"><code>make build-cli
./bin/trelay config set api-url http://localhost:8080
./bin/trelay config set api-key YOUR_API_KEY</code></pre>
	<p>Replace <code>http://localhost:8080</code> with your server URL and <code>YOUR_API_KEY</code> with the value of <code>API_KEY</code> from your server <code>.env</code>.</p>

	<h2>Commands</h2>

	<h3>trelay create &lt;url&gt;</h3>
	<p>Create a short link. The long URL is required; all other options are optional.</p>
	<table>
		<thead>
			<tr>
				<th>Flag / option</th>
				<th>Description</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td><code>--slug</code></td>
				<td>Custom slug (e.g. <code>my-link</code>)</td>
			</tr>
			<tr>
				<td><code>--expires</code></td>
				<td>Expiration (e.g. <code>30d</code>, <code>24h</code>)</td>
			</tr>
			<tr>
				<td><code>--password</code></td>
				<td>Prompt for a password to protect the link</td>
			</tr>
			<tr>
				<td><code>--one-time</code></td>
				<td>Link works only once, then is invalidated</td>
			</tr>
			<tr>
				<td><code>--folder-id</code></td>
				<td>ID of folder to put the link in</td>
			</tr>
		</tbody>
	</table>
	<pre class="code-block"><code>trelay create https://example.com/page --slug docs
trelay create https://example.com/secret --password --expires 7d</code></pre>

	<h3>trelay list</h3>
	<p>List all links. Supports search and filters via flags (e.g. <code>--search</code>, <code>--folder-id</code>). Output format: <code>--format table</code> (default), <code>--format json</code>, or <code>--format csv</code>.</p>
	<pre class="code-block"><code>trelay list
trelay list --format json
trelay list --search "docs"</code></pre>

	<h3>trelay get &lt;slug&gt;</h3>
	<p>Get details for a single link by slug.</p>
	<pre class="code-block"><code>trelay get my-link</code></pre>

	<h3>trelay delete &lt;slug&gt;</h3>
	<p>Delete a link (soft-delete by default; use <code>--permanent</code> for hard delete).</p>
	<pre class="code-block"><code>trelay delete my-link
trelay delete my-link --permanent</code></pre>

	<h3>trelay stats &lt;slug&gt;</h3>
	<p>View click statistics for a link. Output: <code>--format table</code>, <code>--format json</code>, or <code>--format csv</code>.</p>
	<pre class="code-block"><code>trelay stats my-link
trelay stats my-link --format json</code></pre>

	<h3>trelay qr &lt;slug&gt;</h3>
	<p>Generate a QR code for the short link. Options: <code>--open</code> to open in browser or system viewer, or copy to clipboard (implementation may vary).</p>
	<pre class="code-block"><code>trelay qr my-link
trelay qr my-link --open</code></pre>

	<h3>trelay folder create &lt;name&gt;</h3>
	<p>Create a folder. Optional <code>--parent-id &lt;id&gt;</code> for a nested folder.</p>
	<pre class="code-block"><code>trelay folder create "Marketing"
trelay folder create "Blog" --parent-id 1</code></pre>

	<h3>trelay folder list</h3>
	<p>List all folders. Output: <code>--format table</code>, <code>--format json</code>, or <code>--format csv</code>.</p>
	<pre class="code-block"><code>trelay folder list</code></pre>

	<h3>trelay config set &lt;key&gt; &lt;value&gt;</h3>
	<p>Set CLI configuration. Keys: <code>api-url</code>, <code>api-key</code>.</p>
	<pre class="code-block"><code>trelay config set api-url https://links.example.com
trelay config set api-key your-api-key</code></pre>

	<h3>trelay completion &lt;shell&gt;</h3>
	<p>Generate shell completion. Supported shells: <code>bash</code>, <code>zsh</code>, <code>fish</code> (if supported by the CLI).</p>
	<pre class="code-block"><code>trelay completion bash   # then source or add to .bashrc
trelay completion zsh    # then source or add to .zshrc</code></pre>

	<h2>Output formats</h2>
	<p>Commands that list or return structured data support <code>--format</code>:</p>
	<ul>
		<li><code>table</code> — Human-readable table (default)</li>
		<li><code>json</code> — JSON (e.g. for piping to <code>jq</code>)</li>
		<li><code>csv</code> — CSV for spreadsheets</li>
	</ul>
	<pre class="code-block"><code>trelay list --format json | jq '.[0]'
trelay stats my-link --format csv > stats.csv</code></pre>

	<h2>Help</h2>
	<p>Run <code>trelay --help</code> for a summary of commands. Use <code>trelay &lt;command&gt; --help</code> for command-specific help.</p>
</DocPage>
