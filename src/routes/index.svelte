<script lang="ts">

	// Imports:
	import Tools from '$lib/Tools.svelte';
	import Navbar from '$lib/Navbar.svelte';
	import Header from '$lib/Header.svelte';
	import Support from '$lib/Support.svelte';
	import Features from '$lib/Features.svelte';
	import Highlights from '$lib/Highlights.svelte';
	import Contributors from '$lib/Contributors.svelte';

	// Links:
	const appLink = 'https://app.weaver.fi';
	const githubLink = 'https://github.com/CookieTrack-io';
	const twitterLink = 'https://twitter.com/cookietrack_io';
	const discordLink = 'https://discord.com/invite/DzADcq7y75';
	const sdkLink = 'https://github.com/CookieTrack-io/weaverfi';

	// Initializations:
	let scrollY = 0;
	
</script>

<!-- #################################################################################################### -->

<!-- SvelteKit Dynamic Header -->
<svelte:head>
	<title>WeaverFi</title>
	<meta name="description" content="The open-source, multi-chain DeFi portfolio tracker." />
</svelte:head>

<!-- Window Bindings -->
<svelte:window bind:scrollY />

<!-- Navbar -->
<Navbar bind:scrollY {twitterLink} {discordLink} {githubLink} />

<!-- Header Section -->
<Header {appLink} />

<!-- Main Highlights -->
<Highlights />

<!-- Blockchain/Project/Token Support -->
<Support />

<!-- Features -->
<Features />

<!-- Tools -->
<Tools />

<!-- Contributors -->
<Contributors {sdkLink} {discordLink} />

<!-- #################################################################################################### -->

<style>

	/* CSS Goes Here */
	
</style>