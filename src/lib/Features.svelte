<section>

	<!-- Dashboard Info -->
	<div>
		<img src="/images/dashboard.svg" alt="Dashboard">
		<h3>Dashboard</h3>
		<span>View your wallet(s) balances all in one place.</span>
	</div>

	<!-- Token Prices Info -->
	<div>
		<img src="/images/txs.svg" alt="Token Prices">
		<h3>Token Prices</h3>
		<span>See current and historical token prices.</span>
	</div>

	<!-- NFTs Info -->
	<div>
		<img src="/images/nfts.svg" alt="NFT Portfolio">
		<h3>NFT Portfolio</h3>
		<span>View your entire NFT collection in all of its glory.</span>
	</div>

	<!-- Fees Info -->
	<div>
		<img src="/images/fees.svg" alt="Gas Fees">
		<h3>Gas Fees</h3>
		<span>Keep track of gas fees on every blockchain.</span>
	</div>

</section>

<!-- #################################################################################################### -->

<style>

	section {
		gap: 3em;
		padding-top: 5em;
		padding-bottom: 5em;
	}

	div {
		text-align: center;
	}

	img {
		height: 4em;
		filter: drop-shadow(0 0 10px var(--primaryColor));
	}

	h3 {
		margin: .5em 0;
		font-size: 1.5em;
	}

	@media screen and (max-width: 800px) {
		section {
			gap: 2em;
		}
	}

	@media screen and (max-width: 700px) {
		section {
			flex-wrap: wrap;
			padding-top: 4em;
		}
		div {
			width: calc(50% - 2em);
			padding: 1em 10%;
		}
	}

	@media screen and (max-width: 600px) {
		div {
			padding: 1em 8%;
		}
	}

	@media screen and (max-width: 400px) {
		div {
			width: 100%;
			padding: 1em 20%;
		}
	}
	
</style>