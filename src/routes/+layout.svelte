<script lang="ts">
	import '../app.css';
	import Nav from '$lib/components/Nav.svelte';
	import Footer from '$lib/components/Footer.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<title>Trelay - Your Links, Your Server</title>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
	<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Martian+Mono:wght@400;500&display=swap" rel="stylesheet">
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
