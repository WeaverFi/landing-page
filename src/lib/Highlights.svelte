<script lang="ts">

	// Initializations & Exports:
	export let sdkLink: string;

</script>

<!-- #################################################################################################### -->

<section>

	<!-- Open Source -->
	<div class="openSource">
		<img src="/images/code.svg" alt="Open Source">
		<div class="content right">
			<h3>Open&#8209;source integrations</h3>
			<span>The SDK that powers WeaverFi is open&#8209;source, allowing anyone to contribute support for new blockchains, protocols or track new tokens.</span>
			<a href="{sdkLink}">Check out the SDK ></a>
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
		<img src="/images/devices.svg" alt="Devices">
		<div class="content right">
			<h3>Use on any device</h3>
			<span>As a progressive web app, you are able to use WeaverFi on any browser, or even download it as an app on your desktop or phone.</span>
		</div>
	</div>

</section>

<!-- #################################################################################################### -->

<style>

	section {
		display: flex;
		flex-direction: column;
		padding: 4em 30vw;
		background-color: var(--terciary-color);
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
		color: var(--accent-color);
	}

	img {
		height: 15em;
	}
	
</style>