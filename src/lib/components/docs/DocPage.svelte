<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		title: string;
		children: Snippet;
	}
	let { title, children }: Props = $props();
</script>

<div class="doc-page">
	<h1 class="doc-title">{title}</h1>
	<div class="doc-prose">
		{@render children()}
	</div>
</div>

<style>
	.doc-page {
		padding-bottom: var(--space-24);
	}

	.doc-title {
		font-size: var(--text-3xl);
		font-weight: 600;
		letter-spacing: -0.02em;
		margin-bottom: var(--space-6);
	}

	.doc-prose {
		font-size: var(--text-base);
		line-height: 1.7;
		color: var(--color-text);
	}

	.doc-prose :global(.lead) {
		font-size: var(--text-lg);
		color: var(--color-text-secondary);
		margin-bottom: var(--space-6);
	}

	.doc-prose :global(h2) {
		font-size: var(--text-xl);
		font-weight: 600;
		margin-top: var(--space-10);
		margin-bottom: var(--space-3);
		padding-bottom: var(--space-2);
		border-bottom: 1px solid var(--color-border-light);
	}

	.doc-prose :global(h3) {
		font-size: var(--text-lg);
		font-weight: 600;
		margin-top: var(--space-6);
		margin-bottom: var(--space-2);
	}

	.doc-prose :global(p) {
		margin-bottom: var(--space-4);
	}

	.doc-prose :global(ul),
	.doc-prose :global(ol) {
		margin-bottom: var(--space-4);
		padding-left: var(--space-6);
	}

	.doc-prose :global(li) {
		margin-bottom: var(--space-2);
	}

	.doc-prose :global(code) {
		font-family: var(--font-mono);
		font-size: 0.9em;
		background: var(--color-bg-subtle);
		padding: 0.12em 0.4em;
		border-radius: var(--radius-sm);
		border: 1px solid var(--color-border-light);
	}

	.doc-prose :global(pre) {
		margin-bottom: var(--space-4);
		overflow-x: auto;
	}

	.doc-prose :global(pre code) {
		display: block;
		padding: var(--space-4);
		background: var(--color-bg-subtle);
		border: 1px solid var(--color-border);
		border-radius: var(--radius-md);
		font-size: var(--text-sm);
		line-height: 1.5;
	}

	.doc-prose :global(.code-block) {
		margin: var(--space-4) 0;
	}

	.doc-prose :global(table) {
		width: 100%;
		border-collapse: collapse;
		font-size: var(--text-sm);
		margin-bottom: var(--space-4);
	}

	.doc-prose :global(th),
	.doc-prose :global(td) {
		text-align: left;
		padding: var(--space-2) var(--space-3);
		border: 1px solid var(--color-border-light);
	}

	.doc-prose :global(th) {
		background: var(--color-bg-subtle);
		font-weight: 600;
	}

	.doc-prose :global(a) {
		color: var(--color-brand);
		text-decoration: none;
	}

	.doc-prose :global(a:hover) {
		text-decoration: underline;
	}
</style>
