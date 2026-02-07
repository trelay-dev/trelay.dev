<script lang="ts">
</script>

<section class="hero">
	<div class="hero-bg">
		<div class="grid-pattern"></div>
	</div>
	
	<div class="hero-content container">
		<div class="badge">
			<span class="badge-dot"></span>
			<span>v2.0 — Now Open Source</span>
		</div>

		<h1 class="hero-title">
			Your Links,<br />
			<span class="gradient-text">Your Server.</span>
		</h1>

		<p class="hero-description">
			A developer-first, privacy-respecting URL manager for self-hosting. Modern web dashboard, powerful CLI, and automation-friendly API.
		</p>

		<div class="hero-actions">
			<a href="https://github.com/trelay-dev/trelay" target="_blank" rel="noopener" class="btn btn-primary">
				<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
					<path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
				</svg>
				Get Started
			</a>
			<a href="#features" class="btn btn-outline">
				Learn More
			</a>
		</div>

		<div class="hero-terminal">
			<div class="terminal-header">
				<div class="terminal-dots">
					<span class="dot red"></span>
					<span class="dot yellow"></span>
					<span class="dot green"></span>
				</div>
				<span class="terminal-title">Terminal</span>
			</div>
			<div class="terminal-body">
				<div class="terminal-line">
					<span class="prompt">$</span>
					<span class="command">trelay create https://example.com/very-long-url --slug my-link</span>
				</div>
				<div class="terminal-line output">
					<span class="success">✓</span> Created: <span class="link">https://yourserver.com/my-link</span>
				</div>
				<div class="terminal-line">
					<span class="prompt">$</span>
					<span class="command">trelay stats my-link</span>
				</div>
				<div class="terminal-line output stats-output">
					<span class="muted">Slug:</span> my-link
				</div>
				<div class="terminal-line output stats-output">
					<span class="muted">Clicks:</span> 1,247 <span class="success">(+23 today)</span>
				</div>
				<div class="terminal-line output stats-output">
					<span class="muted">Created:</span> 7 days ago
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	.hero {
		position: relative;
		padding: calc(64px + var(--space-16)) 0 var(--space-20);
		overflow: hidden;
		min-height: 100vh;
		display: flex;
		align-items: center;
	}

	.hero-bg {
		position: absolute;
		inset: 0;
		z-index: -1;
	}

	.grid-pattern {
		position: absolute;
		inset: 0;
		background-image: 
			linear-gradient(var(--color-border-light) 1px, transparent 1px),
			linear-gradient(90deg, var(--color-border-light) 1px, transparent 1px);
		background-size: 48px 48px;
		opacity: 0.6;
		mask-image: radial-gradient(ellipse 80% 60% at 50% 40%, black 0%, transparent 70%);
		-webkit-mask-image: radial-gradient(ellipse 80% 60% at 50% 40%, black 0%, transparent 70%);
	}

	.hero-content {
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
	}

	.badge {
		display: inline-flex;
		align-items: center;
		gap: var(--space-2);
		padding: var(--space-2) var(--space-4);
		background: var(--color-bg-elevated);
		border: 1px solid var(--color-border);
		border-radius: var(--radius-full);
		font-size: var(--text-sm);
		color: var(--color-text-secondary);
		margin-bottom: var(--space-8);
	}

	.badge-dot {
		width: 8px;
		height: 8px;
		background: var(--color-brand);
		border-radius: 50%;
		animation: pulse 2s ease-in-out infinite;
	}

	@keyframes pulse {
		0%, 100% { opacity: 1; }
		50% { opacity: 0.5; }
	}

	.hero-title {
		font-size: var(--text-5xl);
		font-weight: 500;
		line-height: 1.05;
		margin-bottom: var(--space-5);
		letter-spacing: -0.03em;
	}

	.gradient-text {
		background: linear-gradient(135deg, var(--color-brand) 0%, var(--color-brand-light) 100%);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		background-clip: text;
	}

	.gradient-text::selection {
		-webkit-text-fill-color: var(--color-bg);
		background: var(--color-brand);
	}

	.hero-description {
		font-size: var(--text-base);
		color: var(--color-text-secondary);
		max-width: 480px;
		margin-bottom: var(--space-6);
		line-height: 1.6;
	}

	.hero-actions {
		display: flex;
		gap: var(--space-4);
		margin-bottom: var(--space-16);
	}

	.btn {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		gap: var(--space-2);
		padding: 10px 20px;
		font-weight: 500;
		font-size: var(--text-sm);
		border-radius: var(--radius-full);
		transition: all var(--transition-fast);
	}

	.btn-primary {
		background: var(--color-text);
		color: var(--color-bg);
	}

	.btn-primary:hover {
		opacity: 0.85;
	}

	.btn-outline {
		background: transparent;
		color: var(--color-text);
		border: 1px solid var(--color-border);
	}

	.btn-outline:hover {
		background: var(--color-bg-elevated);
	}

	.hero-terminal {
		width: 100%;
		max-width: 600px;
		background: var(--color-bg-elevated);
		border: 1px solid var(--color-border);
		border-radius: var(--radius-lg);
		overflow: hidden;
		box-shadow: var(--shadow-lg);
		text-align: left;
	}

	.terminal-header {
		display: flex;
		align-items: center;
		gap: var(--space-4);
		padding: var(--space-3) var(--space-4);
		background: var(--color-bg-subtle);
		border-bottom: 1px solid var(--color-border);
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
		color: var(--color-text-muted);
	}

	.terminal-body {
		padding: var(--space-4);
		font-family: var(--font-mono);
		font-size: var(--text-sm);
	}

	.terminal-line {
		display: flex;
		align-items: flex-start;
		gap: var(--space-2);
		margin-bottom: var(--space-2);
	}

	.terminal-line.output {
		color: var(--color-text-secondary);
		padding-left: var(--space-4);
	}

	.prompt {
		color: var(--color-brand);
		font-weight: 600;
	}

	.command {
		color: var(--color-text);
	}

	.success {
		color: #27ca40;
	}

	.link {
		color: var(--color-brand);
	}

	.stats-output .muted {
		color: #666;
	}

	.stats-output .success {
		color: #27ca40;
	}

	@media (max-width: 768px) {
		.hero {
			padding: calc(64px + var(--space-12)) 0 var(--space-12);
			min-height: auto;
		}

		.hero-title {
			font-size: var(--text-4xl);
		}

		.hero-description {
			font-size: var(--text-base);
		}

		.hero-actions {
			flex-direction: column;
			width: 100%;
			max-width: 280px;
		}

		.btn {
			width: 100%;
		}

		.hero-terminal {
			max-width: 100%;
		}

		.terminal-body {
			overflow-x: auto;
		}
	}
</style>
