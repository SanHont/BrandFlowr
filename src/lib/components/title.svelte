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
	<img src="assets/wave.svg" alt="" loading="lazy" />
</section>

<style>
	h1 {
		z-index: 10;
		font-size: 25rem;
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
		margin-top: -14rem;
	}

	img {
		margin-top: -8rem;
		display: block;
	}

	@media only screen and (max-width: 1250px) {
		h1 {
			font-size: 20rem;
		}

		.flowr {
			margin-top: -11rem;
		}
	}

	@media only screen and (max-width: 1000px) {
		h1 {
			margin-top: 5rem;
			margin-bottom: 5rem;
			font-size: 15rem;
		}

		.flowr {
			margin-top: -8rem;
		}
	}

	@media only screen and (max-width: 750px) {
		h1 {
			margin-top: 11rem;
			margin-bottom: 11rem;
			font-size: 10rem;
		}
		.flowr {
			margin-top: -5rem;
		}

		img {
			margin-top: -5rem;
		}
	}

	@media only screen and (max-width: 500px) {
		h1 {
			margin-top: 15.5rem;
			margin-bottom: 15.5rem;
			font-size: 7rem;
		}
		.flowr {
			margin-top: -4rem;
		}

		img {
			margin-top: -4rem;
		}
	}

	@media only screen and (max-width: 390px) {
		h1 {
			margin-top: 17rem;
			margin-bottom: 17rem;
			font-size: 6rem;
		}

		.flowr {
			margin-top: -3rem;
		}

		img {
			margin-top: -4rem;
		}
	}
</style>
