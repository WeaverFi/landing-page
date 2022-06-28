<script lang="ts">

	// Imports:
	import weaver from 'weaverfi';

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
		<img src="" alt="Tokens">

		<!-- SDK Values -->
		<div class="numbers">
			<span class="value">{chainCount}</span>
			<span class="label">blockchains</span>
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
		display: flex;
	}
	
</style>