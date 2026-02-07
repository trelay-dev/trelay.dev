<script lang="ts">
	import DocPage from '$lib/components/docs/DocPage.svelte';
</script>

<svelte:head>
	<title>API Reference — Trelay Docs</title>
	<meta name="description" content="Trelay REST API: authentication, links, folders, stats, preview, and redirect." />
</svelte:head>

<DocPage title="API Reference">
	<p class="lead">
		Trelay exposes a REST API for links, folders, stats, preview, and import/export. All endpoints except health checks and redirects require authentication via API key or JWT.
	</p>

	<h2>Base URL</h2>
	<p>Use your server URL as the base, e.g. <code>http://localhost:8080</code> or <code>https://links.example.com</code>.</p>

	<h2>Authentication</h2>
	<p>Use one of:</p>
	<ul>
		<li><strong>API key</strong> — Send header <code>X-API-Key: YOUR_API_KEY</code> on every request.</li>
		<li><strong>JWT</strong> — Login via <code>POST /api/v1/auth/login</code> with <code>{'{"api_key":"YOUR_API_KEY"}'}</code>, then send <code>Authorization: Bearer &lt;token&gt;</code> on subsequent requests.</li>
	</ul>
	<p>Redirects (<code>{'GET /{slug}'}</code>) and <code>GET /healthz</code> do not require auth.</p>

	<h2>Endpoints</h2>

	<h3>Health</h3>
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
				<td><code>/healthz</code></td>
				<td>Health check. Returns <code>{'{"status":"ok"}'}</code>.</td>
			</tr>
		</tbody>
	</table>

	<h3>Auth</h3>
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
				<td><code>/api/v1/auth/login</code></td>
				<td>Login with API key. Body: <code>{'{"api_key":"YOUR_API_KEY"}'}</code>. Returns <code>token</code> and <code>expires_at</code>.</td>
			</tr>
		</tbody>
	</table>

	<h3>Links</h3>
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
				<td><code>/api/v1/links</code></td>
				<td>Create link. Body: <code>url</code> (required), <code>slug</code>, <code>domain</code>, <code>password</code>, <code>ttl_hours</code>, <code>tags</code>, <code>folder_id</code>, <code>is_one_time</code>.</td>
			</tr>
			<tr>
				<td>GET</td>
				<td><code>/api/v1/links</code></td>
				<td>List links. Query: <code>search</code>, <code>folder_id</code>, <code>limit</code>, <code>offset</code>, <code>include_deleted</code>, <code>only_deleted</code>, <code>created_after</code>, <code>created_before</code>.</td>
			</tr>
			<tr>
				<td>GET</td>
				<td><code>{'/api/v1/links/{slug}'}</code></td>
				<td>Get link by slug.</td>
			</tr>
			<tr>
				<td>PATCH</td>
				<td><code>{'/api/v1/links/{slug}'}</code></td>
				<td>Update link. Body: <code>url</code>, <code>password</code>, <code>ttl_hours</code>, <code>tags</code>, <code>folder_id</code>.</td>
			</tr>
			<tr>
				<td>DELETE</td>
				<td><code>{'/api/v1/links/{slug}'}</code></td>
				<td>Delete link (soft-delete). Query: <code>permanent=true</code> for hard delete.</td>
			</tr>
			<tr>
				<td>POST</td>
				<td><code>{'/api/v1/links/{slug}/restore'}</code></td>
				<td>Restore a soft-deleted link.</td>
			</tr>
			<tr>
				<td>DELETE</td>
				<td><code>/api/v1/links</code></td>
				<td>Bulk delete. Body: <code>{'{"slugs":["a","b"]}'}</code>, optional <code>permanent</code>.</td>
			</tr>
		</tbody>
	</table>

	<h3>Redirect (no auth)</h3>
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
				<td><code>{'/{slug}'}</code></td>
				<td>Redirect to original URL. Query: <code>password</code> if link is password-protected.</td>
			</tr>
		</tbody>
	</table>

	<h3>Folders</h3>
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
				<td><code>/api/v1/folders</code></td>
				<td>List folders.</td>
			</tr>
			<tr>
				<td>POST</td>
				<td><code>/api/v1/folders</code></td>
				<td>Create folder. Body: <code>name</code> (required), <code>parent_id</code>.</td>
			</tr>
			<tr>
				<td>GET</td>
				<td><code>{'/api/v1/folders/{id}'}</code></td>
				<td>Get folder by ID.</td>
			</tr>
			<tr>
				<td>DELETE</td>
				<td><code>{'/api/v1/folders/{id}'}</code></td>
				<td>Delete folder.</td>
			</tr>
		</tbody>
	</table>

	<h3>Stats</h3>
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
				<td><code>{'/api/v1/stats/{slug}'}</code></td>
				<td>Get click stats. Query: <code>period</code>, <code>export=csv</code> or <code>export=json</code> for file download.</td>
			</tr>
			<tr>
				<td>GET</td>
				<td><code>{'/api/v1/stats/{slug}/daily'}</code></td>
				<td>Daily click breakdown.</td>
			</tr>
			<tr>
				<td>GET</td>
				<td><code>{'/api/v1/stats/{slug}/referrers'}</code></td>
				<td>Top referrers.</td>
			</tr>
		</tbody>
	</table>

	<h3>Preview</h3>
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
				<td><code>/api/v1/preview?url=</code></td>
				<td>Fetch Open Graph metadata for a URL. Returns <code>title</code>, <code>description</code>, <code>image_url</code>, <code>fetched_at</code>.</td>
			</tr>
		</tbody>
	</table>

	<h3>Import & Export</h3>
	<p>See <a href="/docs/import-export">Import & Export</a> for CSV/JSON import and export endpoints.</p>

	<h2>Response format</h2>
	<p>Success responses are JSON with <code>success: true</code> and <code>data</code> containing the result. List endpoints may include <code>meta</code> with <code>total</code>, <code>limit</code>, <code>offset</code>.</p>
	<pre class="code-block"><code>{`{
  "success": true,
  "data": { ... }
}`}</code></pre>
	<p>Errors return appropriate HTTP status and a body like:</p>
	<pre class="code-block"><code>{`{
  "success": false,
  "error": {
    "code": "validation_error",
    "message": "url is required",
    "field": "url"
  }
}`}</code></pre>

	<h2>OpenAPI spec</h2>
	<p>The full OpenAPI 3.0 spec is in the repo at <code>api/openapi.yaml</code>. You can use it with Swagger UI, Postman, or code generators.</p>
</DocPage>
