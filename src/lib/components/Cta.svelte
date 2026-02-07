<script lang="ts">
	const CTA_CODE = `git clone https://github.com/trelay-dev/trelay.git
cd trelay
cp env.example .env
docker compose up -d`;

	let copied = $state(false);

	async function copyToClipboard() {
		try {
			await navigator.clipboard.writeText(CTA_CODE);
			copied = true;
			setTimeout(() => (copied = false), 2000);
		} catch {
			// fallback for older browsers
			const ta = document.createElement('textarea');
			ta.value = CTA_CODE;
			ta.setAttribute('readonly', '');
			ta.style.position = 'absolute';
			ta.style.left = '-9999px';
			document.body.appendChild(ta);
			ta.select();
			try {
				document.execCommand('copy');
				copied = true;
				setTimeout(() => (copied = false), 2000);
			} finally {
				document.body.removeChild(ta);
			}
		}
	}
</script>

<section class="cta">
	<div class="container">
		<div class="cta-content">
			<h2 class="cta-title">Ready to take control of your links?</h2>
			<p class="cta-description">
				Clone, set your .env (API_KEY, JWT_SECRET), and run. Self-hosted, open source, MIT licensed.
			</p>
			
		<div class="cta-code">
			<button type="button" class="copy-btn" aria-label="Copy to clipboard" onclick={copyToClipboard} title={copied ? 'Copied!' : 'Copy'}
				>{#if copied}
					<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
						<polyline points="20 6 9 17 4 12"></polyline>
					</svg>
				{:else}
					<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
						<rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect>
						<path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"></path>
					</svg>
				{/if}
			</button>
			<code>{CTA_CODE}</code>
		</div>

			<div class="cta-actions">
				<a href="https://github.com/trelay-dev/trelay" target="_blank" rel="noopener" class="btn btn-primary">
					<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
						<path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
					</svg>
					View on GitHub
				</a>
			<a href="/docs/installation" class="btn btn-outline">
				Quick Start
			</a>
			</div>
		</div>
	</div>
</section>

<style>
	.cta {
		padding: var(--space-24) 0;
		background: var(--color-bg-subtle);
	}

	.cta-content {
		text-align: center;
		max-width: 600px;
		margin: 0 auto;
	}

	.cta-title {
		font-size: var(--text-3xl);
		font-weight: 500;
		margin-bottom: var(--space-4);
		letter-spacing: -0.02em;
	}

	.cta-description {
		font-size: var(--text-base);
		color: var(--color-text-secondary);
		margin-bottom: var(--space-6);
		line-height: 1.6;
	}

	.cta-code {
		position: relative;
		display: inline-block;
		text-align: left;
		background: var(--color-bg-elevated);
		border: 1px solid var(--color-border);
		border-radius: var(--radius-md);
		padding: var(--space-4) var(--space-12) var(--space-4) var(--space-4);
		margin-bottom: var(--space-8);
		max-width: 100%;
	}

	.cta-code code {
		font-family: var(--font-mono);
		font-size: var(--text-sm);
		color: var(--color-text);
		white-space: pre;
		display: block;
		line-height: 1.6;
	}

	.copy-btn {
		position: absolute;
		top: var(--space-2);
		right: var(--space-2);
		display: flex;
		align-items: center;
		justify-content: center;
		padding: var(--space-2);
		color: var(--color-text-muted);
		background: var(--color-bg-subtle);
		border-radius: var(--radius-sm);
		transition: color var(--transition-fast), background var(--transition-fast);
	}

	.copy-btn:hover {
		color: var(--color-text);
		background: var(--color-border-light);
	}

	.cta-actions {
		display: flex;
		justify-content: center;
		gap: var(--space-4);
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

	@media (max-width: 640px) {
		.cta {
			padding: var(--space-16) 0;
		}

		.cta-title {
			font-size: var(--text-3xl);
		}

		.cta-code {
			padding: var(--space-4);
			padding-right: var(--space-10);
		}

		.cta-code code {
			font-size: var(--text-xs);
			overflow-x: auto;
		}

		.cta-actions {
			flex-direction: column;
		}
	}
</style>
