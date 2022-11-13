<script lang="ts">

	// Initializations & Exports:
	export let sdkLink: string;
	export let apiLink: string;

</script>

<!-- #################################################################################################### -->

<section>

	<!-- Open Source -->
	<div class="openSource">
		<img src="/images/integrations.svg" alt="Open Source">
		<div class="content right">
			<h3>Open&#8209;source integrations</h3>
			<span>The SDK that powers WeaverFi is open&#8209;source, allowing anyone to contribute support for new blockchains, protocols or track new tokens.</span>
			<a href="{sdkLink}" target="__blank">Check out the SDK ></a>
		</div>
	</div>

	<!-- Privacy -->
	<div class="privacy">
		<div class="content left">
			<h3>Complete privacy</h3>
			<span>This is not Web 2.0. Your data is maintained locally on your browser and there is no intrusive ads, trackers, or any database collecting user data.</span>
		</div>
		<img src="/images/safe.svg" alt="Privacy">
	</div>

	<!-- Devices -->
	<div class="devices">
		<img src="/images/compatibility.svg" alt="Devices">
		<div class="content right">
			<h3>Use on any device</h3>
			<span>As a progressive web app, you are able to use WeaverFi on any browser, or even download it as an app on your desktop or phone.</span>
		</div>
	</div>

	<!-- API -->
	<div class="api">
		<div class="content left">
			<h3>Open API</h3>
			<span>Take advantage of the <i>easiest</i> way to interact with the WeaverFi SDK.</span>
			<a href="{apiLink}" target="__blank">Check out the API ></a>
		</div>
		<img src="/images/api.svg" alt="API">
	</div>

</section>

<!-- #################################################################################################### -->

<style>

	section {
		flex-direction: column;
		padding: 4em 30vw;
		background-color: var(--tertiaryColor);
	}

	section > div {
		display: flex;
		align-items: center;
		margin: 2em 0;
	}

	div.content {
		display: flex;
		flex-direction: column;
		flex: 1;
		padding: 2em 0;
	}

	div.content.left {
		padding-right: 4em;
	}

	div.content.right {
		padding-left: 4em;
	}

	h3 {
		margin-bottom: .5em;
		font-size: 2em;
	}

	a {
		margin-top: 1em;
		color: var(--accentColor);
	}

	img {
		height: 15em;
	}

	@media screen and (max-width: 1270px) {
		section {
			padding: 4em 26vw;
		}
	}

	@media screen and (max-width: 1000px) {
		section {
			padding: 4em 22vw;
		}
	}

	@media screen and (max-width: 800px) {
		section {
			padding: 4em 18vw;
		}
	}

	@media screen and (max-width: 700px) {
		section {
			padding: 4em 14vw;
		}
	}

	@media screen and (max-width: 600px) {
		section {
			padding: 4em 10vw;
		}
	}

	@media screen and (max-width: 500px) {
		section {
			padding: 4em 6vw;
		}
		div.content.left {
			padding-right: 2em;
		}
		div.content.right {
			padding-left: 2em;
		}
	}

	@media screen and (max-width: 450px) {
		section {
			gap: 2em;
		}
		section > div {
			flex-direction: column;
			margin: 0;
		}
		div.content {
			padding: 1em 0 !important;
		}
		div.content.left {
			order: 1;
		}
	}
	
</style>