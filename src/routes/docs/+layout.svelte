<script lang="ts">
	import { page } from '$app/stores';

	const nav = [
		{ label: 'Overview', href: '/docs' },
		{ label: 'Installation', href: '/docs/installation' },
		{ label: 'Configuration', href: '/docs/configuration' },
		{ label: 'CLI Reference', href: '/docs/cli' },
		{ label: 'API Reference', href: '/docs/api' },
		{ label: 'Import & Export', href: '/docs/import-export' }
	];
</script>

<div class="docs-layout">
	<aside class="docs-sidebar">
		<div class="sidebar-header">
			<a href="/docs" class="sidebar-title">Documentation</a>
		</div>
		<nav class="sidebar-nav">
			{#each nav as item}
				<a
					href={item.href}
					class="sidebar-link"
					class:active={$page.url.pathname === item.href}
				>
					{item.label}
				</a>
			{/each}
		</nav>
		<div class="sidebar-footer">
			<a href="/" class="back-home">← Back to home</a>
		</div>
	</aside>
	<article class="docs-content">
		<slot />
	</article>
</div>

<style>
	.docs-layout {
		display: grid;
		grid-template-columns: 240px 1fr;
		gap: var(--space-12);
		min-height: calc(100vh - 64px);
		padding: var(--space-8) var(--space-6);
		margin-top: 64px;
		max-width: var(--container-max);
		margin-left: auto;
		margin-right: auto;
	}

	.docs-sidebar {
		position: sticky;
		top: calc(64px + var(--space-8));
		height: fit-content;
		padding: var(--space-5);
		background: var(--color-bg-elevated);
		border: 1px solid var(--color-border-light);
		border-radius: var(--radius-lg);
	}

	.sidebar-header {
		margin-bottom: var(--space-4);
	}

	.sidebar-title {
		font-weight: 600;
		font-size: var(--text-sm);
		color: var(--color-text);
		text-decoration: none;
	}

	.sidebar-title:hover {
		color: var(--color-brand);
	}

	.sidebar-nav {
		display: flex;
		flex-direction: column;
		gap: var(--space-1);
	}

	.sidebar-link {
		font-size: var(--text-sm);
		color: var(--color-text-secondary);
		text-decoration: none;
		padding: var(--space-2) var(--space-3);
		border-radius: var(--radius-md);
		transition: color var(--transition-fast), background var(--transition-fast);
	}

	.sidebar-link:hover {
		color: var(--color-text);
		background: var(--color-bg-subtle);
	}

	.sidebar-link.active {
		color: var(--color-brand);
		font-weight: 500;
		background: color-mix(in srgb, var(--color-brand) 12%, transparent);
	}

	.sidebar-footer {
		margin-top: var(--space-6);
		padding-top: var(--space-4);
		border-top: 1px solid var(--color-border-light);
	}

	.back-home {
		font-size: var(--text-xs);
		color: var(--color-text-muted);
		text-decoration: none;
	}

	.back-home:hover {
		color: var(--color-brand);
	}

	.docs-content {
		min-width: 0;
		max-width: 720px;
	}

	@media (max-width: 900px) {
		.docs-layout {
			grid-template-columns: 1fr;
			padding: var(--space-6) var(--space-4);
		}

		.docs-sidebar {
			position: static;
			display: block;
			padding: var(--space-4);
			border-radius: var(--radius-md);
		}

		.sidebar-header {
			margin-bottom: var(--space-3);
		}

		.sidebar-nav {
			display: grid;
			grid-template-columns: repeat(2, minmax(0, 1fr));
			gap: var(--space-2);
		}

		.sidebar-link {
			padding: var(--space-2) var(--space-3);
			border: 1px solid transparent;
			text-align: center;
			font-size: var(--text-xs);
		}

		.sidebar-link.active {
			border-color: color-mix(in srgb, var(--color-brand) 30%, transparent);
		}

		.sidebar-footer {
			margin-top: var(--space-4);
		}
	}

	@media (max-width: 640px) {
		.docs-layout {
			padding: var(--space-5) var(--space-3);
			gap: var(--space-6);
		}

		.docs-sidebar {
			padding: var(--space-3);
		}

		.sidebar-title {
			font-size: var(--text-xs);
		}

		.sidebar-nav {
			grid-template-columns: 1fr;
		}

		.sidebar-link {
			text-align: left;
		}
	}
</style>
