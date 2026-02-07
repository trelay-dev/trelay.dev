<script lang="ts">
	import { onMount } from 'svelte';

	let theme = $state<'light' | 'dark'>('light');
	let mobileMenuOpen = $state(false);
	let scrolled = $state(false);

	onMount(() => {
		const stored = localStorage.getItem('theme');
		if (stored === 'dark' || (!stored && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
			theme = 'dark';
			document.documentElement.setAttribute('data-theme', 'dark');
		}

		const handleScroll = () => {
			scrolled = window.scrollY > 20;
		};
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function toggleTheme() {
		theme = theme === 'light' ? 'dark' : 'light';
		document.documentElement.setAttribute('data-theme', theme);
		localStorage.setItem('theme', theme);
	}

	function toggleMobileMenu() {
		mobileMenuOpen = !mobileMenuOpen;
	}

	function closeMobileMenu() {
		mobileMenuOpen = false;
	}
</script>

<nav class="nav" class:scrolled>
	<div class="nav-container container">
		<a href="/" class="logo" onclick={closeMobileMenu}>
			<img src="/logo.png" alt="Trelay" class="logo-img" />
			<span class="logo-text">Trelay</span>
		</a>

		<div class="nav-links" class:open={mobileMenuOpen}>
			<a href="/#features" class="nav-link" onclick={closeMobileMenu}>Features</a>
			<a href="/#cli" class="nav-link" onclick={closeMobileMenu}>CLI</a>
			<a href="/#comparison" class="nav-link" onclick={closeMobileMenu}>Compare</a>
			<a href="/docs" class="nav-link" onclick={closeMobileMenu}>Docs</a>
		</div>

		<div class="nav-actions">
			<button class="theme-toggle" onclick={toggleTheme} aria-label="Toggle theme">
				{#if theme === 'light'}
					<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
						<path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path>
					</svg>
				{:else}
					<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
						<circle cx="12" cy="12" r="5"></circle>
						<line x1="12" y1="1" x2="12" y2="3"></line>
						<line x1="12" y1="21" x2="12" y2="23"></line>
						<line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line>
						<line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line>
						<line x1="1" y1="12" x2="3" y2="12"></line>
						<line x1="21" y1="12" x2="23" y2="12"></line>
						<line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line>
						<line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line>
					</svg>
				{/if}
			</button>

			<a href="https://github.com/trelay-dev/trelay" target="_blank" rel="noopener" class="btn btn-secondary btn-sm github-btn">
				<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="currentColor">
					<path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
				</svg>
				<span>GitHub</span>
			</a>

			<button class="mobile-toggle" onclick={toggleMobileMenu} aria-label="Toggle menu">
				{#if mobileMenuOpen}
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
						<line x1="18" y1="6" x2="6" y2="18"></line>
						<line x1="6" y1="6" x2="18" y2="18"></line>
					</svg>
				{:else}
					<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
						<line x1="3" y1="12" x2="21" y2="12"></line>
						<line x1="3" y1="6" x2="21" y2="6"></line>
						<line x1="3" y1="18" x2="21" y2="18"></line>
					</svg>
				{/if}
			</button>
		</div>
	</div>
</nav>

<style>
	.nav {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 100;
		background: transparent;
		transition: background var(--transition-base), box-shadow var(--transition-base);
	}

	.nav.scrolled {
		background: var(--color-bg-elevated);
		box-shadow: var(--shadow-sm);
		border-bottom: 1px solid var(--color-border-light);
	}

	.nav-container {
		display: flex;
		align-items: center;
		justify-content: space-between;
		height: 64px;
	}

	.logo {
		display: flex;
		align-items: center;
		gap: var(--space-2);
		font-weight: 600;
		font-size: var(--text-lg);
	}

	.logo-img {
		width: 32px;
		height: 32px;
	}

	.logo-text {
		color: var(--color-text);
	}

	.nav-links {
		display: flex;
		align-items: center;
		gap: var(--space-8);
	}

	.nav-link {
		font-size: var(--text-sm);
		color: var(--color-text-secondary);
		transition: color var(--transition-fast);
		font-weight: 500;
	}

	.nav-link:hover {
		color: var(--color-text);
	}

	.nav-actions {
		display: flex;
		align-items: center;
		gap: var(--space-3);
	}

	.theme-toggle {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 36px;
		height: 36px;
		border-radius: var(--radius-md);
		color: var(--color-text-secondary);
		transition: background var(--transition-fast), color var(--transition-fast);
	}

	.theme-toggle:hover {
		background: var(--color-bg-subtle);
		color: var(--color-text);
	}

	.btn {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		gap: var(--space-2);
		font-weight: 500;
		border-radius: var(--radius-full);
		transition: all var(--transition-fast);
	}

	.btn-sm {
		padding: 6px 14px;
		font-size: var(--text-xs);
	}

	.btn-secondary {
		background: var(--color-text);
		color: var(--color-bg);
		border: 1px solid var(--color-text);
	}

	.btn-secondary:hover {
		opacity: 0.85;
	}

	.mobile-toggle {
		display: none;
		align-items: center;
		justify-content: center;
		width: 40px;
		height: 40px;
		color: var(--color-text);
	}

	@media (max-width: 768px) {
		.nav-links {
			position: fixed;
			top: 64px;
			left: 0;
			right: 0;
			flex-direction: column;
			background: var(--color-bg-elevated);
			padding: var(--space-6);
			gap: var(--space-4);
			border-bottom: 1px solid var(--color-border);
			transform: translateY(-100%);
			opacity: 0;
			pointer-events: none;
			transition: transform var(--transition-base), opacity var(--transition-base);
		}

		.nav-links.open {
			transform: translateY(0);
			opacity: 1;
			pointer-events: auto;
		}

		.nav-link {
			font-size: var(--text-base);
			padding: var(--space-2) 0;
		}

		.github-btn span {
			display: none;
		}

		.mobile-toggle {
			display: flex;
		}
	}
</style>
