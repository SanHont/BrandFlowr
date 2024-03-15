<script>
	import { onMount } from 'svelte';

	import { gsap } from 'gsap';

	onMount(() => {
		gsap.fromTo('.brand', { x: -4000 }, { x: 0, duration: 1 });
		gsap.fromTo('.flowr', { x: 4000 }, { x: 0, duration: 1 });
	});

	// import { ScrollTrigger } from "gsap/ScrollTrigger";

	// gsap.registerPlugin(ScrollTrigger);
</script>

<section>
	<h1><span class="brand">BRAND</span><span class="flowr">FLOWR</span></h1>
	<img src="assets/wave.svg" alt="Your SVG" />
</section>

<style>
	h1 {
		z-index: 10;
		font-size: 25rem;
		/* font-family: 'Protest Strike', sans-serif;
		font-weight: 800;
		font-style: normal; */
		font-family: 'Anton', sans-serif;
		font-weight: 400;
		font-style: normal;
		margin-top: -2rem;
		margin-left: 2rem;
	}

	h1 span {
		display: block;
	}

	.flowr {
		margin-top: -15rem;
	}

	img {
		display: block;
	}
</style>
