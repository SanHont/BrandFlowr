<script>
	import Socials from '../lib/components/socials.svelte';
</script>

<section>
	<h1>Brand<span>Flowr</span></h1>
</section>

<Socials />

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

	h1 {
		font-size: 25rem;
	}

	h1 span {
		display: block;
		margin-top: -10%;
	}
</style>
