<script lang="ts">

	// Initializations & Exports:
	export let appLink: string;
	const launched = false;

</script>

<!-- #################################################################################################### -->

<section>

	<!-- Header Content -->
	<div class="content">
		<h2>The open&#8209;source, multi&#8209;chain DeFi portfolio tracker</h2>
		{#if launched}
			<span>Try out WeaverFi for free today</span>
			<a href="{appLink}">
				<strong>Go to App</strong>
				<i class="icofont-arrow-right" />
			</a>
		{:else}
			<span></span>
			<a href="/" style="cursor: not-allowed;"><strong>Coming Soon</strong></a>
		{/if}
	</div>

	<!-- Weavey -->
	<img src="/images/happyWeavey.svg" alt="Happy Weavey">

</section>

<!-- #################################################################################################### -->

<style>

	section {
		margin-top: 5em;
		padding-top: 5em;
		padding-bottom: 5em;
	}

	div.content {
		display: flex;
		flex-direction: column;
		justify-content: center;
		flex: 1;
		padding-right: 1em;
	}

	div.content > h2 {
		font-size: 3.5em;
	}

	div.content > span {
		margin: 1em 0;
		font-size: 1.8em;
	}

	div.content > a {
		width: 12em;
		margin-bottom: 2em;
		padding: .8em;
		font-size: 1.2em;
		color: var(--secondaryColor);
		background-color: var(--accentColor);
		border: 3px solid var(--accentColor);
		border-radius: 2em;
		text-align: center;
		text-decoration: none;
		transition: all .3s ease-out;
	}

	div.content > a:hover {
		color: white;
		background-color: var(--primaryColor);
	}

	img {
		height: 35em;
	}

	@media screen and (max-width: 900px) {
		img {
			height: 30em;
		}
	}

	@media screen and (max-width: 700px) {
		section {
			flex-direction: column;
		}
	}
	
</style>