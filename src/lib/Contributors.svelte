<script lang="ts">

	// Initializations:
	export let contributeLink: string;
	export let discordLink: string;

</script>

<!-- #################################################################################################### -->

<section>

	<!-- Weavey -->
	<img src="/images/readingWeavey.svg" alt="Reading Weavey">

	<!-- Content -->
	<div class="content">

		<!-- Title -->
		<h2>Want to join us in growing our web?</h2>
	
		<!-- SDK -->
		<div>
			<h3>Contribute to our open-source SDK</h3>
			<span>Adding support for new blockchains, projects or tokens has never been easier.</span>
			<a href="{contributeLink}" target="__blank">
				<strong>Contribute</strong>
				<i class="icofont-arrow-right" />
			</a>
		</div>
	
		<!-- Discord -->
		<div>
			<h3>Chat with us on Discord</h3>
			<span>Want to discuss DeFi events? Suggest improvements to the platform? This is the place to be.</span>
			<a href="{discordLink}" target="__blank">
				<strong>Join the chat</strong>
				<i class="icofont-arrow-right" />
			</a>
		</div>

	</div>
	
</section>

<!-- #################################################################################################### -->

<style>

	section {
		position: relative;
		flex-direction: column;
		padding: 5em 18em 10em;
		background-color: var(--terciary-color);
	}

	img {
		position: absolute;
		top: -1em;
		right: calc(50% + 1em);
		height: 42em;
	}

	div.content {
		display: flex;
		flex-direction: column;
		padding-left: calc(50% + 1em);
	}

	div.content div {
		display: flex;
		flex-direction: column;
		margin: 2em 12em 2em 2em;
	}

	h2 {
		margin-bottom: .5em;
		font-size: 2em;
	}

	h3 {
		margin-bottom: .5em;
		font-size: 1.5em;
	}

	a {
		width: 12em;
		margin-top: 1em;
		padding: .6em;
		font-size: 1.2em;
		color: var(--secondary-color);
		background-color: var(--accent-color);
		border: 3px solid var(--accent-color);
		border-radius: 2em;
		text-align: center;
		text-decoration: none;
		transition: all .3s ease-out;
	}

	a:hover {
		color: white;
		background-color: var(--primary-color);
	}
	
</style>