<script lang="ts">
	import type { Snippet } from 'svelte';

	interface Props {
		title: string;
		children: Snippet;
	}
	let { title, children }: Props = $props();

	function copyCodeBlock(node: HTMLElement) {
		const addCopyButtons = () => {
			const blocks = node.querySelectorAll('pre.code-block');
			blocks.forEach((pre) => {
				if ((pre as HTMLElement).dataset.copyBtnAdded === 'true') return;
				const code = pre.querySelector('code');
				if (!code) return;
				const text = code.textContent ?? '';
				const btn = document.createElement('button');
				btn.type = 'button';
				btn.className = 'doc-copy-btn';
				btn.setAttribute('aria-label', 'Copy to clipboard');
				btn.innerHTML = `<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"></path></svg>`;
				btn.onclick = async () => {
					try {
						await navigator.clipboard.writeText(text);
						btn.classList.add('copied');
						btn.innerHTML = `<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="20 6 9 17 4 12"></polyline></svg>`;
						setTimeout(() => {
							btn.classList.remove('copied');
							btn.innerHTML = `<svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"></path></svg>`;
						}, 2000);
					} catch {
						const ta = document.createElement('textarea');
						ta.value = text;
						ta.style.position = 'absolute';
						ta.style.left = '-9999px';
						document.body.appendChild(ta);
						ta.select();
						try {
							document.execCommand('copy');
							btn.classList.add('copied');
						} finally {
							document.body.removeChild(ta);
						}
					}
				};
				pre.appendChild(btn);
				(pre as HTMLElement).dataset.copyBtnAdded = 'true';
			});
		};
		addCopyButtons();
		const obs = new MutationObserver(addCopyButtons);
		obs.observe(node, { childList: true, subtree: true });
		return {
			destroy() {
				obs.disconnect();
			}
		};
	}
</script>

<div class="doc-page">
	<h1 class="doc-title">{title}</h1>
	<div class="doc-prose" use:copyCodeBlock>
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

	.doc-prose :global(pre.code-block) {
		position: relative;
		margin-bottom: var(--space-4);
		overflow-x: auto;
		padding: var(--space-4) var(--space-12) var(--space-4) var(--space-4);
		background: var(--color-bg-elevated);
		border: 1px solid var(--color-border);
		border-radius: var(--radius-md);
	}

	.doc-prose :global(pre.code-block code) {
		display: block;
		padding: 0;
		background: transparent;
		border: none;
		border-radius: 0;
		font-size: var(--text-sm);
		line-height: 1.5;
		font-family: var(--font-mono);
		color: var(--color-text);
	}

	.doc-prose :global(.doc-copy-btn) {
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
		cursor: pointer;
		transition: color var(--transition-fast), background var(--transition-fast);
	}

	.doc-prose :global(.doc-copy-btn:hover) {
		color: var(--color-text);
		background: var(--color-border-light);
	}

	.doc-prose :global(.doc-copy-btn.copied) {
		color: #27ca40;
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
