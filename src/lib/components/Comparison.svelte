<script lang="ts">
	const competitors = ['Trelay', 'Bitly', 'YOURLS', 'Shlink'];
	
	const features = [
		{ name: 'Self-hosted', values: [true, false, true, true] },
		{ name: 'Modern UI', values: [true, true, false, 'partial'] },
		{ name: 'CLI Tool', values: [true, false, false, true] },
		{ name: 'Privacy-first', values: [true, false, true, true] },
		{ name: 'Single container', values: [true, null, true, false] },
		{ name: 'One-time links', values: [true, false, false, true] },
		{ name: 'Free forever', values: [true, false, true, true] },
		{ name: 'Open source', values: [true, false, true, true] }
	];
</script>

<section id="comparison" class="comparison">
	<div class="container">
		<div class="section-header">
			<span class="section-label">Compare</span>
			<h2 class="section-title">How Trelay stacks up</h2>
			<p class="section-description">
				See how we compare to other URL shorteners. Spoiler: we're the only one that gives you everything.
			</p>
		</div>

		<div class="table-wrapper">
			<table class="comparison-table">
				<thead>
					<tr>
						<th class="feature-col">Feature</th>
						{#each competitors as competitor, i}
							<th class:highlight={i === 0}>{competitor}</th>
						{/each}
					</tr>
				</thead>
				<tbody>
					{#each features as feature}
						<tr>
							<td class="feature-name">{feature.name}</td>
							{#each feature.values as value, i}
								<td class:highlight={i === 0}>
									{#if value === true}
										<span class="check">
											<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
												<polyline points="20 6 9 17 4 12"></polyline>
											</svg>
										</span>
									{:else if value === false}
										<span class="cross">
											<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
												<line x1="18" y1="6" x2="6" y2="18"></line>
												<line x1="6" y1="6" x2="18" y2="18"></line>
											</svg>
										</span>
									{:else if value === 'partial'}
										<span class="partial">Partial</span>
									{:else}
										<span class="na">—</span>
									{/if}
								</td>
							{/each}
						</tr>
					{/each}
				</tbody>
			</table>
		</div>
	</div>
</section>

<style>
	.comparison {
		padding: var(--space-24) 0;
		background: var(--color-bg);
	}

	.section-header {
		text-align: center;
		max-width: 600px;
		margin: 0 auto var(--space-12);
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

	.table-wrapper {
		overflow-x: auto;
		border-radius: var(--radius-lg);
		border: 1px solid var(--color-border-light);
		background: var(--color-bg-elevated);
	}

	.comparison-table {
		width: 100%;
		border-collapse: collapse;
		font-size: var(--text-sm);
	}

	.comparison-table th,
	.comparison-table td {
		padding: var(--space-4) var(--space-5);
		text-align: center;
		border-bottom: 1px solid var(--color-border-light);
	}

	.comparison-table th {
		font-weight: 600;
		background: var(--color-bg-subtle);
		color: var(--color-text-secondary);
	}

	.comparison-table th.highlight {
		color: var(--color-brand);
		background: linear-gradient(180deg, rgba(233, 30, 99, 0.08) 0%, rgba(233, 30, 99, 0.02) 100%);
	}

	.comparison-table td.highlight {
		background: linear-gradient(180deg, rgba(233, 30, 99, 0.04) 0%, rgba(233, 30, 99, 0.01) 100%);
	}

	.comparison-table tbody tr:last-child td {
		border-bottom: none;
	}

	.comparison-table tbody tr:hover {
		background: var(--color-bg-subtle);
	}

	.comparison-table tbody tr:hover td.highlight {
		background: linear-gradient(180deg, rgba(233, 30, 99, 0.08) 0%, rgba(233, 30, 99, 0.04) 100%);
	}

	.feature-col,
	.feature-name {
		text-align: left !important;
		font-weight: 500;
	}

	.check {
		display: inline-flex;
		color: #27ca40;
	}

	.cross {
		display: inline-flex;
		color: var(--color-text-muted);
	}

	.partial {
		font-size: var(--text-xs);
		color: var(--color-text-muted);
	}

	.na {
		color: var(--color-text-muted);
	}

	@media (max-width: 640px) {
		.comparison {
			padding: var(--space-16) 0;
		}

		.section-title {
			font-size: var(--text-3xl);
		}

		.comparison-table th,
		.comparison-table td {
			padding: var(--space-3);
			font-size: var(--text-xs);
		}
	}
</style>
