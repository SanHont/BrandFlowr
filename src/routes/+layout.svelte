<main>
	<slot />
</main>

<style>
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	:global(html) {
		scroll-behavior: smooth;
	}

	:global(body) {
		background-color: var(--background-color);
		color: var(--text-color);
		position: relative;
	}
</style>
