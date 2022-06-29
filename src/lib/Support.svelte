<script lang="ts">

	// Imports:
	import weaver from 'weaverfi';
	import TokenWeb from './TokenWeb.svelte';

	// SDK Values:
	const chains = weaver.getAllChains();
	const chainCount = chains.length;
	const projects = weaver.getAllProjects();
	const projectCount = Object.values(projects).reduce((sum, pList) => sum + pList.length, 0);
	const tokens = weaver.getAllTokens();
	const tokenCount = Object.values(tokens).reduce((sum, tList) => sum + tList.length, 0);

</script>

<!-- #################################################################################################### -->

<section>

	<!-- Title -->
	<h2>Unrivaled scalability throughout the DeFi ecosystem</h2>

	<!-- Content -->
	<div class="content">

		<!-- Token Image -->
		<TokenWeb />

		<!-- SDK Values -->
		<div class="numbers">
			<span class="value">{chainCount}</span>
			<span class="label">chains</span>
			<span class="value">{projectCount}</span>
			<span class="label">defi projects</span>
			<span class="value">{tokenCount}</span>
			<span class="label">tokens tracked</span>
		</div>

	</div>
	
</section>

<!-- #################################################################################################### -->

<style>

	section {
		flex-direction: column;
		padding-top: 5em;
		padding-bottom: 5em;
		color: var(--secondary-color);
		background-color: var(--accent-color);
	}

	h2 {
		font-size: 2em;
		text-align: center;
	}

	div.content {
		display: flex;
		margin-top: 4em;
	}

	img {
		flex: 1;
	}

	div.numbers {
		display: flex;
		flex-direction: column;
		padding: 0 1em;
	}

	span.value {
		margin-top: 1em;
		font-size: 2em;
		font-weight: bold;
	}
	
</style>