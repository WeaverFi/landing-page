<script lang="ts">

	// Initializations:
	export let sdkLink: string;
	export let discordLink: string;

</script>

<!-- #################################################################################################### -->

<section>

	<!-- Title -->
	<h2>Want to join us in growing our web?</h2>

	<!-- Content -->
	<div class="content">

		<!-- Weavey -->
		<img src="/images/readingWeavey.svg" alt="Reading Weavey">
		
		<!-- Options List -->
		<div class="list">
			<h3>Contribute to our open-source SDK</h3>
			<span>Adding support for new blockchains, projects or tokens has never been easier.</span>
			<a href="{sdkLink}"><button>Contribute</button></a>
			<h3>Chat with us on Discord</h3>
			<span>Want to discuss DeFi events? Suggest improvements to the platform? This is the place to be.</span>
			<a href="{discordLink}"><button>Join the chat</button></a>
		</div>

	</div>
	
</section>

<!-- #################################################################################################### -->

<style>

	section {
		display: flex;
	}
	
</style>