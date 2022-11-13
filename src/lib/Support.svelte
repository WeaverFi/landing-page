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

	<!-- Token Web -->
	<TokenWeb />

	<!-- Title -->
	<h2>Unrivaled scalability throughout the DeFi ecosystem</h2>

	<!-- Content -->
	<div class="content">

		<!-- SDK Values -->
		<div class="numbers">
			<div>
				<span class="value">{chainCount}</span>
				<span class="label">chains</span>
			</div>
			<div>
				<span class="value">{projectCount}</span>
				<span class="label">defi projects</span>
			</div>
			<div>
				<span class="value">{tokenCount}</span>
				<span class="label">tokens tracked</span>
			</div>
		</div>

	</div>
	
</section>

<!-- #################################################################################################### -->

<style>

	section {
		position: relative;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding-top: 5em;
		padding-bottom: 5em;
		color: var(--secondaryColor);
		background-color: var(--accentColor);
		box-shadow: 0 0 20px black;
	}

	section > * {
		z-index: 1;
	}

	h2 {
		font-size: 2em;
		text-align: center;
		text-shadow: 1px 1px 2px var(--fontColor);
	}

	div.content {
		display: flex;
		margin-top: 4em;
	}

	div.numbers {
		display: flex;
		flex-direction: row;
		justify-content: center;
		gap: 4em;
		padding: 0 1em;
	}

	div.numbers div {
		display: flex;
		flex-direction: column;
		min-width: 10em;
		padding: 5px 15px;
		text-align: center;
		background-color: hsla(0, 0%, 100%, 0.25);
		border: 2px solid var(--fontColor);
		border-radius: 1em;
		backdrop-filter: blur(5px);
		overflow: hidden;
	}

	span.value {
		font-size: 2em;
		font-weight: bold;
	}

	span.label {
		font-weight: bold;
	}

	@media screen and (max-width: 700px) {
		div.content {
			flex-direction: row;
			margin-top: 0;
		}
		div.numbers {
			flex-direction: column;
			justify-content: center;
			align-items: stretch;
			padding: 1em 0 0;
			gap: 2em;
			margin-top: 2em;
		}
		div.numbers div {
			flex-direction: column;
			justify-content: center;
			align-items: center;
		}
		span.value {
			margin: 0 .2em 0 .5em;
		}
		span.value:first-of-type {
			margin-left: 0;
		}
		span.label {
			margin-bottom: .2em;
			font-size: 1.2em;
		}
	}

	@media screen and (max-width: 400px) {
		div.numbers {
			flex-wrap: wrap;
			padding-top: 2em;
		}
		div.numbers div {
			justify-content: center;
			width: 100%;
		}
		span.value {
			margin-left: 0;
		}
	}
	
</style>