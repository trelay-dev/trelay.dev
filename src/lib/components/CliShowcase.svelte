<script lang="ts">
	const commands = [
		{ cmd: 'trelay create', desc: 'Create short links with options' },
		{ cmd: 'trelay list', desc: 'List and filter your links' },
		{ cmd: 'trelay stats', desc: 'View click analytics' },
		{ cmd: 'trelay qr', desc: 'Generate QR codes' },
		{ cmd: 'trelay folder', desc: 'Organize with folders' },
		{ cmd: 'trelay config', desc: 'Configure CLI settings' }
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
							<code class="command-code">
								<span class="cmd-name">{cmd.split(' ')[0]}</span>
								{#if cmd.split(' ').length > 1}
									<span class="cmd-action"> {cmd.split(' ').slice(1).join(' ')}</span>
								{/if}
							</code>
							<span class="command-desc">{desc}</span>
						</div>
					{/each}
				</div>

				<a href="/docs/cli" class="btn btn-secondary">
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
						<span class="command">
							<span class="cmd-name">trelay</span> <span class="cmd-action">create</span> <span class="url">https://docs.example.com/api/v2</span> <span class="line-cont">\</span>
						</span>
					</div>
					<div class="terminal-line continuation">
						<span class="flag">--slug</span> <span class="value">docs</span> <span class="flag">--expires</span> <span class="value">30d</span> <span class="flag">--password</span>
					</div>
					<div class="terminal-line output">
						<span class="muted">Password:</span> <span class="hidden-text">••••••••</span>
					</div>
					<div class="terminal-line output success-line">
						<span class="success">✓</span> Created link
					</div>
					<div class="terminal-line output">
						<span class="muted">URL:</span> <span class="link">https://trl.sh/docs</span>
					</div>
					<div class="terminal-line output">
						<span class="muted">Expires:</span> <span class="value">2026-03-07</span>
					</div>
					<div class="terminal-line output">
						<span class="muted">Protected:</span> <span class="success">Yes</span>
					</div>
					<div class="terminal-line spacer"></div>
					<div class="terminal-line">
						<span class="prompt">$</span>
						<span class="command">
							<span class="cmd-name">trelay</span> <span class="cmd-action">list</span> <span class="flag">--format</span> <span class="value">json</span> <span class="pipe">|</span> <span class="cmd-name">jq</span> <span class="string">'.[0]'</span>
						</span>
					</div>
					<div class="terminal-line output json-output">
						<pre><span class="json-brace">&#123;</span>
  <span class="json-key">"slug"</span>: <span class="json-string">"docs"</span>,
  <span class="json-key">"url"</span>: <span class="json-string">"https://docs.example.com/api/v2"</span>,
  <span class="json-key">"clicks"</span>: <span class="json-number">0</span>,
  <span class="json-key">"created"</span>: <span class="json-string">"2026-02-05T14:30:00Z"</span>
<span class="json-brace">&#125;</span></pre>
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
		white-space: nowrap;
		flex-shrink: 0;
	}

	.command-code .cmd-name {
		color: var(--color-brand);
		font-weight: 500;
	}

	.command-code .cmd-action {
		color: #6ea8fe;
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

	.cmd-name {
		color: #f5f5f5;
		font-weight: 500;
	}

	.cmd-action {
		color: #6ea8fe;
	}

	.url {
		color: var(--color-syntax-url);
	}

	.line-cont {
		color: #666;
	}

	.flag {
		color: #6ea8fe;
	}

	.value {
		color: #a0a0a0;
	}

	.pipe {
		color: #666;
	}

	.string {
		color: var(--color-syntax-url);
	}

	.link {
		color: var(--color-brand);
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

	.json-key {
		color: #6ea8fe;
	}

	.json-string {
		color: var(--color-syntax-url);
	}

	.json-number {
		color: #f5f5f5;
	}

	.json-brace {
		color: #a0a0a0;
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
