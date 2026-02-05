<script lang="ts">
	const commands = [
		{ cmd: 'trelay create', desc: 'Create short links with all options' },
		{ cmd: 'trelay list', desc: 'List and search your links' },
		{ cmd: 'trelay stats', desc: 'View analytics with export' },
		{ cmd: 'trelay qr', desc: 'Generate QR codes' },
		{ cmd: 'trelay folder', desc: 'Organize with folders' },
		{ cmd: 'trelay config', desc: 'Configure API and settings' }
	];
</script>

<section id="cli" class="cli-showcase">
	<div class="container">
		<div class="cli-grid">
			<div class="cli-content">
				<span class="section-label">CLI</span>
				<h2 class="section-title">Command-line<br />first design</h2>
				<p class="section-description">
					Manage everything from your terminal. Pipe support, multiple output formats (table, JSON, CSV), and shell completions.
				</p>

				<div class="commands-list">
					{#each commands as { cmd, desc }}
						<div class="command-item">
							<code class="command-code">{cmd}</code>
							<span class="command-desc">{desc}</span>
						</div>
					{/each}
				</div>

				<a href="https://github.com/trelay-dev/trelay#cli" target="_blank" rel="noopener" class="btn btn-secondary">
					View CLI Docs
					<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
						<line x1="7" y1="17" x2="17" y2="7"></line>
						<polyline points="7 7 17 7 17 17"></polyline>
					</svg>
				</a>
			</div>

			<div class="cli-terminal">
				<div class="terminal-header">
					<div class="terminal-dots">
						<span class="dot red"></span>
						<span class="dot yellow"></span>
						<span class="dot green"></span>
					</div>
					<span class="terminal-title">trelay-cli</span>
				</div>
				<div class="terminal-body">
					<div class="terminal-line">
						<span class="prompt">$</span>
						<span class="command">trelay create https://docs.example.com/api/v2 \</span>
					</div>
					<div class="terminal-line continuation">
						<span class="flag">--slug</span> docs <span class="flag">--expires</span> 30d <span class="flag">--password</span>
					</div>
					<div class="terminal-line output">
						<span class="muted">Password:</span> <span class="hidden-text">••••••••</span>
					</div>
					<div class="terminal-line output success-line">
						<span class="success">✓</span> Created link
					</div>
					<div class="terminal-line output">
						<span class="muted">URL:</span> https://trl.sh/docs
					</div>
					<div class="terminal-line output">
						<span class="muted">Expires:</span> 2026-03-07
					</div>
					<div class="terminal-line output">
						<span class="muted">Protected:</span> <span class="success">Yes</span>
					</div>
					<div class="terminal-line spacer"></div>
					<div class="terminal-line">
						<span class="prompt">$</span>
						<span class="command">trelay list --format json | jq '.[0]'</span>
					</div>
					<div class="terminal-line output json-output">
						<pre>{`{
  "slug": "docs",
  "url": "https://docs.example.com/api/v2",
  "clicks": 0,
  "created": "2026-02-05T14:30:00Z"
}`}</pre>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	.cli-showcase {
		padding: var(--space-24) 0;
		background: var(--color-bg-subtle);
	}

	.cli-grid {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: var(--space-12);
		align-items: center;
	}

	.cli-content {
		max-width: 480px;
	}

	.section-label {
		display: inline-block;
		font-size: var(--text-sm);
		font-weight: 500;
		color: var(--color-brand);
		margin-bottom: var(--space-4);
		text-transform: uppercase;
		letter-spacing: 0.05em;
	}

	.section-title {
		font-size: var(--text-3xl);
		font-weight: 500;
		margin-bottom: var(--space-4);
		letter-spacing: -0.02em;
	}

	.section-description {
		font-size: var(--text-base);
		color: var(--color-text-secondary);
		line-height: 1.7;
		margin-bottom: var(--space-8);
	}

	.commands-list {
		display: flex;
		flex-direction: column;
		gap: var(--space-3);
		margin-bottom: var(--space-8);
	}

	.command-item {
		display: flex;
		align-items: center;
		gap: var(--space-4);
	}

	.command-code {
		font-family: var(--font-mono);
		font-size: var(--text-sm);
		background: var(--color-bg-elevated);
		padding: var(--space-1) var(--space-3);
		border-radius: var(--radius-sm);
		border: 1px solid var(--color-border-light);
		color: var(--color-brand);
		white-space: nowrap;
	}

	.command-desc {
		font-size: var(--text-sm);
		color: var(--color-text-secondary);
	}

	.btn {
		display: inline-flex;
		align-items: center;
		gap: var(--space-2);
		padding: 10px 18px;
		font-weight: 500;
		font-size: var(--text-xs);
		border-radius: var(--radius-full);
		transition: all var(--transition-fast);
	}

	.btn-secondary {
		background: transparent;
		color: var(--color-text);
		border: 1px solid var(--color-border);
	}

	.btn-secondary:hover {
		background: var(--color-bg-elevated);
	}

	.cli-terminal {
		background: #1a1a1a;
		border-radius: var(--radius-lg);
		overflow: hidden;
		box-shadow: var(--shadow-lg);
	}

	.terminal-header {
		display: flex;
		align-items: center;
		gap: var(--space-4);
		padding: var(--space-3) var(--space-4);
		background: #141414;
		border-bottom: 1px solid #2a2a2a;
	}

	.terminal-dots {
		display: flex;
		gap: var(--space-2);
	}

	.dot {
		width: 12px;
		height: 12px;
		border-radius: 50%;
	}

	.dot.red { background: #ff5f56; }
	.dot.yellow { background: #ffbd2e; }
	.dot.green { background: #27ca40; }

	.terminal-title {
		font-size: var(--text-xs);
		color: #666;
	}

	.terminal-body {
		padding: var(--space-4);
		font-family: var(--font-mono);
		font-size: var(--text-sm);
		color: #f5f5f5;
	}

	.terminal-line {
		display: flex;
		align-items: flex-start;
		gap: var(--space-2);
		margin-bottom: var(--space-1);
		line-height: 1.5;
	}

	.terminal-line.continuation {
		padding-left: var(--space-4);
		color: #a0a0a0;
	}

	.terminal-line.output {
		padding-left: var(--space-4);
		color: #a0a0a0;
	}

	.terminal-line.spacer {
		height: var(--space-4);
	}

	.prompt {
		color: var(--color-brand);
		font-weight: 600;
	}

	.command {
		color: #f5f5f5;
	}

	.flag {
		color: #6ea8fe;
	}

	.muted {
		color: #666;
	}

	.hidden-text {
		color: #a0a0a0;
	}

	.success {
		color: #27ca40;
	}

	.success-line {
		color: #f5f5f5;
	}

	.json-output pre {
		color: #a0a0a0;
		font-size: var(--text-xs);
		line-height: 1.4;
		margin: 0;
	}

	@media (max-width: 1024px) {
		.cli-grid {
			grid-template-columns: 1fr;
			gap: var(--space-8);
		}

		.cli-content {
			max-width: 100%;
			text-align: center;
		}

		.commands-list {
			align-items: center;
		}

		.command-item {
			flex-direction: column;
			gap: var(--space-1);
		}
	}

	@media (max-width: 640px) {
		.cli-showcase {
			padding: var(--space-16) 0;
		}

		.section-title {
			font-size: var(--text-3xl);
		}

		.terminal-body {
			overflow-x: auto;
		}
	}
</style>
