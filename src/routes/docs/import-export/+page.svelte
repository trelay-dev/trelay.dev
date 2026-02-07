<script lang="ts">
	import DocPage from '$lib/components/docs/DocPage.svelte';
</script>

<svelte:head>
	<title>Import & Export — Trelay Docs</title>
	<meta name="description" content="Import links from CSV or JSON; export links and stats to CSV or JSON." />
</svelte:head>

<DocPage title="Import & Export">
	<p class="lead">
		Trelay supports importing links from CSV or JSON (including from other URL shorteners) and exporting links or per-link stats to CSV or JSON.
	</p>

	<h2>Export links</h2>
	<p>Export all links (or filtered by folder) as CSV or JSON. Requires authentication (<code>X-API-Key</code> or <code>Authorization: Bearer &lt;token&gt;</code>).</p>

	<h3>Endpoint</h3>
	<table>
		<thead>
			<tr>
				<th>Method</th>
				<th>Endpoint</th>
				<th>Description</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>GET</td>
				<td><code>/api/v1/export</code></td>
				<td>Export links. Query: <code>format=csv</code> or <code>format=json</code>, optional <code>folder_id</code>.</td>
			</tr>
		</tbody>
	</table>

	<h3>Example</h3>
	<pre class="code-block"><code>curl -H "X-API-Key: YOUR_API_KEY" \
  "http://localhost:8080/api/v1/export?format=json" -o links.json

curl -H "X-API-Key: YOUR_API_KEY" \
  "http://localhost:8080/api/v1/export?format=csv&folder_id=1" -o folder1.csv</code></pre>

	<h2>Export stats</h2>
	<p>Export click statistics for a single link as CSV or JSON via the stats endpoint.</p>
	<table>
		<thead>
			<tr>
				<th>Method</th>
				<th>Endpoint</th>
				<th>Description</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>GET</td>
				<td><code>{'/api/v1/stats/{slug}?export=csv'}</code></td>
				<td>Download stats as CSV.</td>
			</tr>
			<tr>
				<td>GET</td>
				<td><code>{'/api/v1/stats/{slug}?export=json'}</code></td>
				<td>Download stats as JSON.</td>
			</tr>
		</tbody>
	</table>

	<h2>Import from CSV</h2>
	<p>Upload a CSV file to create many links at once. The API accepts a multipart form with <code>file</code> and optional <code>format</code> and <code>skip_duplicates</code>.</p>

	<h3>Endpoint</h3>
	<table>
		<thead>
			<tr>
				<th>Method</th>
				<th>Endpoint</th>
				<th>Description</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>POST</td>
				<td><code>/api/v1/import</code></td>
				<td>Import from CSV. Form: <code>file</code> (required), <code>format</code> (generic, yourls, shlink, bitly), <code>skip_duplicates</code> (true/false). Optional query: <code>folder_id</code>.</td>
			</tr>
		</tbody>
	</table>

	<h3>CSV formats</h3>
	<ul>
		<li><code>generic</code> — Generic CSV: columns like <code>url</code>, <code>slug</code>, <code>tags</code>, etc. Header row is auto-detected; column names can vary (e.g. <code>url</code>, <code>long_url</code>, <code>destination</code>).</li>
		<li><code>yourls</code> — YOURLS-style export.</li>
		<li><code>shlink</code> — Shlink-style export.</li>
		<li><code>bitly</code> — Bitly-style export.</li>
	</ul>
	<p>When <code>skip_duplicates</code> is <code>true</code>, links with a slug that already exists are skipped instead of causing an error.</p>

	<h3>Example (generic CSV)</h3>
	<pre class="code-block"><code># CSV with header: url, slug, tags, ...
url,slug,tags
https://example.com/page1,page1,"blog,docs"
https://example.com/page2,page2,"blog"</code></pre>
	<pre class="code-block"><code>curl -X POST -H "X-API-Key: YOUR_API_KEY" \
  -F "file=@links.csv" \
  -F "format=generic" \
  -F "skip_duplicates=true" \
  http://localhost:8080/api/v1/import</code></pre>

	<h2>Import from JSON</h2>
	<p>Send a JSON body with an array of link objects. Each object must have <code>url</code>; other fields are optional.</p>

	<h3>Endpoint</h3>
	<table>
		<thead>
			<tr>
				<th>Method</th>
				<th>Endpoint</th>
				<th>Description</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>POST</td>
				<td><code>/api/v1/import/json</code></td>
				<td>Import from JSON. Body: <code>{'{"links": [...], "skip_duplicates": true}'}</code>. Each link: <code>url</code> (required), <code>slug</code>, <code>tags</code>, <code>password</code>, <code>ttl_hours</code>, <code>folder_id</code>.</td>
			</tr>
		</tbody>
	</table>

	<h3>Example</h3>
	<pre class="code-block"><code>{`{
  "links": [
    { "url": "https://example.com/a", "slug": "link-a", "tags": ["blog"] },
    { "url": "https://example.com/b", "slug": "link-b" }
  ],
  "skip_duplicates": true
}`}</code></pre>
	<pre class="code-block"><code>{`curl -X POST -H "X-API-Key: YOUR_API_KEY" \\
  -H "Content-Type: application/json" \\
  -d '{"links":[{"url":"https://example.com/a","slug":"link-a"}],"skip_duplicates":true}' \\
  http://localhost:8080/api/v1/import/json`}</code></pre>

	<h2>Import response</h2>
	<p>Import endpoints return a result object:</p>
	<pre class="code-block"><code>{`{
  "success": true,
  "data": {
    "total": 10,
    "imported": 8,
    "skipped": 1,
    "failed": 1,
    "errors": [
      { "row": 5, "url": "https://...", "slug": "x", "message": "slug already exists" }
    ]
  }
}`}</code></pre>
	<p><code>total</code> is the number of rows/items processed; <code>imported</code>, <code>skipped</code>, and <code>failed</code> sum to <code>total</code>. <code>errors</code> lists failed rows with reason.</p>
</DocPage>
