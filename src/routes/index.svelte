<script>

	// Imports:
	import { onMount } from 'svelte';

	// Initializations:
	const sdkRepo = 'https://github.com/CookieTrack-io/weaverfi';

	onMount(() => {
		// :3
	});
	
</script>

<!-- #################################################################################################### -->

<!-- SvelteKit Dynamic Header -->
<svelte:head>
	<title>WeaverFi</title>
	<meta name="description" content="The open-source, multi-chain DeFi portfolio tracker." />
</svelte:head>

<!-- Temporary Section -->
<section class="temporary">
	<img src="/images/weavey.png" alt="Weavey">
	<span>WeaverFi is coming.</span>
	<span class="sdk">Contribute to building our open-source SDK on <a href="{sdkRepo}">GitHub</a>.</span>
</section>

<!-- #################################################################################################### -->

<style>

	section {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.temporary {
		flex-direction: column;
		height: 100vh;
	}

	.temporary > img {
		height: 20em;
	}

	.temporary > span {
		margin-top: 2em;
		padding: 0 10vw;
		text-align: center;
	}
	
</style>