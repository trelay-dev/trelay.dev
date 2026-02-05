<script lang="ts">
	import '../app.css';
	import { inject } from '@vercel/analytics';
	import Nav from '$lib/components/Nav.svelte';
	import Footer from '$lib/components/Footer.svelte';

	inject();

	let { children } = $props();
</script>

<svelte:head>
	<title>Trelay - Your Links, Your Server</title>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@400;500;600;700&family=Martian+Mono:wght@400;500&display=swap" rel="stylesheet">
</svelte:head>

<Nav />

<main>
	{@render children()}
</main>

<Footer />

<style>
	main {
		min-height: 100vh;
	}
</style>
