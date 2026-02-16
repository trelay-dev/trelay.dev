<script lang="ts">
	const currentYear = new Date().getFullYear();
</script>

<footer class="footer">
	<div class="container">
		<div class="footer-content">
			<div class="footer-brand">
				<a href="/" class="logo">
					<img src="/logo.png" alt="Trelay" class="logo-img" />
					<span class="logo-text">Trelay</span>
				</a>
				<p class="footer-tagline">
					Developer-first URL shortener.<br />
					Self-hosted. Open source. Private.
				</p>
			</div>

			<div class="footer-links">
				<div class="footer-group">
					<h4 class="footer-heading">Product</h4>
					<nav class="footer-nav">
						<a href="#features">Features</a>
						<a href="#cli">CLI</a>
						<a href="#comparison">Compare</a>
					</nav>
				</div>

				<div class="footer-group">
					<h4 class="footer-heading">Resources</h4>
					<nav class="footer-nav">
						<a href="/docs">Documentation</a>
						<a href="/docs/installation">Quick Start</a>
						<a href="/docs/api">API Reference</a>
						<a href="https://github.com/trelay-dev/trelay/releases" target="_blank" rel="noopener">Releases</a>
					</nav>
				</div>

				<div class="footer-group">
					<h4 class="footer-heading">Community</h4>
					<nav class="footer-nav">
						<a href="https://github.com/trelay-dev/trelay" target="_blank" rel="noopener">GitHub</a>
						<a href="https://github.com/trelay-dev/trelay/issues" target="_blank" rel="noopener">Issues</a>
						<a href="https://github.com/trelay-dev/trelay/discussions" target="_blank" rel="noopener">Discussions</a>
					</nav>
				</div>
			</div>
		</div>

		<div class="footer-bottom">
			<p class="copyright">
				&copy; {currentYear} Trelay. Released under the MIT License.
			</p>
			<div class="footer-social">
				<a href="https://github.com/trelay-dev/trelay" target="_blank" rel="noopener" aria-label="GitHub">
					<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
						<path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
					</svg>
				</a>
			</div>
		</div>
	</div>
</footer>

<style>
	.footer {
		padding: var(--space-16) 0 var(--space-8);
		background: var(--color-bg);
		border-top: 1px solid var(--color-border-light);
	}

	.footer-content {
		display: grid;
		grid-template-columns: 1.5fr 2fr;
		gap: var(--space-12);
		margin-bottom: var(--space-12);
	}

	.logo {
		display: inline-flex;
		align-items: center;
		gap: var(--space-2);
		margin-bottom: var(--space-4);
	}

	.logo-img {
		width: 28px;
		height: 28px;
	}

	.logo-text {
		font-weight: 600;
		font-size: var(--text-lg);
	}

	.footer-tagline {
		font-size: var(--text-sm);
		color: var(--color-text-secondary);
		line-height: 1.6;
	}

	.footer-links {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: var(--space-8);
	}

	.footer-heading {
		font-size: var(--text-sm);
		font-weight: 600;
		margin-bottom: var(--space-4);
		color: var(--color-text);
	}

	.footer-nav {
		display: flex;
		flex-direction: column;
		gap: var(--space-3);
	}

	.footer-nav a {
		font-size: var(--text-sm);
		color: var(--color-text-secondary);
		transition: color var(--transition-fast);
	}

	.footer-nav a:hover {
		color: var(--color-text);
	}

	.footer-bottom {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding-top: var(--space-8);
		border-top: 1px solid var(--color-border-light);
	}

	.copyright {
		font-size: var(--text-sm);
		color: var(--color-text-muted);
	}

	.footer-social {
		display: flex;
		gap: var(--space-4);
	}

	.footer-social a {
		color: var(--color-text-muted);
		transition: color var(--transition-fast);
	}

	.footer-social a:hover {
		color: var(--color-text);
	}

	@media (max-width: 768px) {
		.footer-content {
			grid-template-columns: 1fr;
			gap: var(--space-8);
		}

		.footer-links {
			grid-template-columns: repeat(2, 1fr);
		}

		.footer-bottom {
			flex-direction: column;
			gap: var(--space-4);
			text-align: center;
		}
	}

	@media (max-width: 480px) {
		.footer-links {
			grid-template-columns: repeat(2, minmax(0, 1fr));
			gap: var(--space-6);
		}

		.logo {
			justify-content: flex-start;
		}

		.footer-group {
			text-align: left;
		}

		.footer-nav {
			align-items: flex-start;
		}
	}
</style>
