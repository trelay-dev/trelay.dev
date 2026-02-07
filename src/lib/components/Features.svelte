<script lang="ts">
	const features = [
		{
			icon: 'link',
			title: 'Link Management',
			description: 'Custom slugs, expiration, password protection, one-time links that self-destruct after first use, and folder organization.'
		},
		{
			icon: 'chart',
			title: 'Privacy-First Analytics',
			description: 'Click analytics with IP anonymization by default. Export to CSV or JSON. Optional custom domain via BASE_URL.'
		},
		{
			icon: 'terminal',
			title: 'Cross-Platform CLI',
			description: 'Create, list, get, delete, stats, and QR from the terminal. Shell completion and table/JSON/CSV output.'
		},
		{
			icon: 'api',
			title: 'REST API',
			description: 'Full API with JWT and API key auth. Links, folders, stats, preview, restore from trash. OpenAPI spec included.'
		},
		{
			icon: 'docker',
			title: 'Single Container',
			description: 'Deploy with Docker Compose. SQLite by default, single binary + frontend. No external dependencies.'
		},
		{
			icon: 'shield',
			title: 'Security Built-in',
			description: 'Rate limiting, secure headers, JWT/API key auth, input validation. No telemetry, no tracking.'
		}
	];
</script>

<section id="features" class="features">
	<div class="container">
		<div class="section-header">
			<span class="section-label">Features</span>
			<h2 class="section-title">Everything you need,<br />nothing you don't</h2>
			<p class="section-description">
				Built for developers who want control over their links without the bloat of enterprise solutions.
			</p>
		</div>

		<div class="features-grid">
			{#each features as feature}
				<div class="feature-card">
					<div class="feature-icon">
						{#if feature.icon === 'link'}
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
								<path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path>
								<path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path>
							</svg>
						{:else if feature.icon === 'chart'}
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
								<line x1="18" y1="20" x2="18" y2="10"></line>
								<line x1="12" y1="20" x2="12" y2="4"></line>
								<line x1="6" y1="20" x2="6" y2="14"></line>
							</svg>
						{:else if feature.icon === 'terminal'}
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
								<polyline points="4 17 10 11 4 5"></polyline>
								<line x1="12" y1="19" x2="20" y2="19"></line>
							</svg>
						{:else if feature.icon === 'api'}
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
								<polyline points="16 18 22 12 16 6"></polyline>
								<polyline points="8 6 2 12 8 18"></polyline>
							</svg>
						{:else if feature.icon === 'docker'}
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
								<rect x="2" y="7" width="20" height="14" rx="2" ry="2"></rect>
								<path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"></path>
							</svg>
						{:else if feature.icon === 'shield'}
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
								<path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"></path>
							</svg>
						{/if}
					</div>
					<h3 class="feature-title">{feature.title}</h3>
					<p class="feature-description">{feature.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	.features {
		padding: var(--space-24) 0;
		background: var(--color-bg);
	}

	.section-header {
		text-align: center;
		max-width: 600px;
		margin: 0 auto var(--space-16);
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
		line-height: 1.6;
	}

	.features-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: var(--space-6);
	}

	.feature-card {
		padding: var(--space-5);
		background: var(--color-bg-elevated);
		border: 1px solid var(--color-border-light);
		border-radius: var(--radius-md);
		transition: border-color var(--transition-fast), box-shadow var(--transition-fast);
	}

	.feature-card:hover {
		border-color: var(--color-border);
		box-shadow: var(--shadow-sm);
	}

	.feature-icon {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 40px;
		height: 40px;
		background: var(--color-bg-subtle);
		border-radius: var(--radius-sm);
		color: var(--color-brand);
		margin-bottom: var(--space-3);
	}

	.feature-icon :global(svg) {
		width: 20px;
		height: 20px;
	}

	.feature-title {
		font-size: var(--text-base);
		font-weight: 500;
		margin-bottom: var(--space-2);
	}

	.feature-description {
		font-size: var(--text-sm);
		color: var(--color-text-secondary);
		line-height: 1.6;
	}

	@media (max-width: 1024px) {
		.features-grid {
			grid-template-columns: repeat(2, 1fr);
		}
	}

	@media (max-width: 640px) {
		.features {
			padding: var(--space-16) 0;
		}

		.section-title {
			font-size: var(--text-3xl);
		}

		.section-description {
			font-size: var(--text-base);
		}

		.features-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
