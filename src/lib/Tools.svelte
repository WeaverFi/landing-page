<section>

	<!-- Title -->
	<h2>. . . and many more analytics and helpful tools:</h2>

	<!-- Tools List -->
	<div class="tools">
		<div>
			<span>Gas Tracker</span>
			<span>Price History</span>
			<span>Yield Finder</span>
			<span>DAO Overviews</span>
		</div>
		<div>
			<span>Token Importer</span>
			<span>Approvals</span>
			<span>DCA Calculator</span>
		</div>
	</div>

</section>

<!-- #################################################################################################### -->

<style>

	section {
		flex-direction: column;
		padding-bottom: 5em;
	}

	h2 {
		margin-bottom: 1em;
		text-align: center;
	}

	div.tools {
		display: flex;
		justify-content: center;
	}

	div.tools div {
		display: flex;
		flex-direction: column;
		padding: 0 2em;
	}

	span {
		margin: .5em 0;
		font-size: 1.2em;
	}

	span::before {
		content: '• ';
		font-weight: bold;
	}

	@media screen and (max-width: 450px) {
		h2 {
			margin: 0 3em 1em;
		}
	}

	@media screen and (max-width: 400px) {
		h2 {
			margin: 0 0 1em;
		}
		div.tools {
			flex-direction: column;
		}
		div.tools div {
			align-items: center;
		}
		span::before {
			content: '';
		}
	}
	
</style>