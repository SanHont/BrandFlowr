<script>
	import Hero from './sections/Hero.svelte';
	import Services from './sections/Services.svelte';
	import Benefits from './sections/Benefits.svelte';
	import Process from './sections/Process.svelte';
	import Testimonials from './sections/Testimonials.svelte';
	import CTA from './sections/CTA.svelte';
	import SocialConnect from './sections/SocialConnect.svelte';
</script>

<main>
	<Hero />
	<Services />
	<Benefits />
	<Process />
	<Testimonials />
	<CTA />
	<SocialConnect />
</main>

<style>
	main {
		font-family: 'Montserrat', sans-serif;
		margin-top: 8rem; /* Space for fixed header */
	}
</style>
