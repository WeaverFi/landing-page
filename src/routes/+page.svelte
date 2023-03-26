<script lang="ts">

	// Imports:
	import Navbar from '$lib/Navbar.svelte';
	import Header from '$lib/Header.svelte';
	import Footer from '$lib/Footer.svelte';
	import Support from '$lib/Support.svelte';
	import Features from '$lib/Features.svelte';
	import Highlights from '$lib/Highlights.svelte';
	import Contributors from '$lib/Contributors.svelte';

	// Links:
	const links = {
		app: 'https://app.weaver.fi',
		api: 'https://api.weaver.fi',
		github: 'https://github.com/WeaverFi',
		twitter: 'https://twitter.com/weaver_fi',
		discord: 'https://discord.com/invite/DzADcq7y75',
		sdk: 'https://github.com/WeaverFi/weaverfi',
		contribute: 'https://github.com/WeaverFi/weaverfi/blob/main/CONTRIBUTING.md',
		gitcoin: 'https://gitcoin.co/grants/5854/weaverfi-the-open-source-defi-portfolio-tracker'
	}

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
<Navbar bind:scrollY twitterLink={links.twitter} discordLink={links.discord} githubLink={links.github} />

<!-- Header Section -->
<Header appLink={links.app} />

<!-- Main Highlights -->
<Highlights sdkLink={links.sdk} apiLink={links.api} />

<!-- Blockchain/Project/Token Support -->
<Support />

<!-- Features -->
<Features />

<!-- Contributors -->
<Contributors contributeLink={links.contribute} discordLink={links.discord} />

<!-- Footer -->
<Footer {links} />