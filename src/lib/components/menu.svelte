<script>
	import { onMount } from 'svelte';

	import { gsap } from 'gsap';

	onMount(() => {
		gsap.fromTo('.icon', { opacity: 0 }, { opacity: 1, duration: 0.7, delay: 1.3 });
		gsap.fromTo('.b', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 0.3 });
		gsap.fromTo('.r', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 0.4 });
		gsap.fromTo('.a', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 0.5 });
		gsap.fromTo('.n', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 0.6 });
		gsap.fromTo('.d', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 0.7 });
		gsap.fromTo('.f', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 0.8 });
		gsap.fromTo('.l', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 0.9 });
		gsap.fromTo('.o', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 1.0 });
		gsap.fromTo('.w', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 1.1 });
		gsap.fromTo('.r2', { opacity: 0 }, { opacity: 1, duration: 0.1, delay: 1.2 });
		gsap.fromTo('.logo', { scale: 1 }, { scale: 0.3, duration: 1, delay: 2.8 });
		gsap.fromTo('.logo', { y: 0 }, { y: -370, duration: 1, delay: 2.8 });
		gsap.fromTo('.navigation', { scale: 0 }, { scale: 1, duration: 1, delay: 2.8 });
		gsap.fromTo('.navigation', { y: -50 }, { y: 0, duration: 1, delay: 2.8 });
		gsap.fromTo('.navigation', { opacity: 0 }, { opacity: 1, duration: 0.7, delay: 2.8 });
	});
</script>

<section>
	<nav class="navigation">
		<div class="left-nav">
			<a href="/">Home</a>
			<a href="/">About Us</a>
		</div>
		<div class="space-between"></div>
		<div class="right-nav">
			<a href="/">Our Work</a>
			<a href="/">Contact</a>
		</div>
	</nav>

	<div class="logo">
		<img class="icon" src="assets/brandflowr-icon.svg" alt="" loading="lazy" />
		<title>
			<h1>
				<span class="b">B</span>
				<span class="r">R</span>
				<span class="a">A</span>
				<span class="n">N</span>
				<span class="d">D</span>
				<span class="flowr">
					<span class="f">F</span>
					<span class="l">L</span>
					<span class="o">O</span>
					<span class="w">W</span>
					<span class="r2">R</span>
				</span>
			</h1>
		</title>
	</div>
</section>

<style>
	title {
		display: flex;
		justify-content: center;
		text-align: center;
	}

	h1 {
		max-width: 100%;
		font-size: 10rem;
		font-family: 'Anton', sans-serif;
		font-weight: 400;
		font-style: normal;
		letter-spacing: -1.3rem;
	}

	.flowr {
		display: block;
		margin-top: -6rem;
	}

	.logo {
		align-items: center;
		display: flex;
		flex-direction: column;
	}

	img {
		width: 23rem;
		margin-bottom: -8rem;
	}

	nav {
		display: flex;
		padding: 1rem;
		margin-top: 4rem;
		justify-content: center;
	}

	a {
		margin: 0 3rem;
		font-family: 'Anton', sans-serif;
		font-weight: 400;
		letter-spacing: 0.04rem;
		font-size: 1.9rem;
		padding: 0 0.2rem;
		text-transform: uppercase;
		text-decoration: none;
		color: var(--text-color);
		border: 3px solid var(--line-color-transparent);
		border-bottom: 3px solid var(--text-color);
		transition: 0.4s;
	}

	a:hover {
		border: 3px solid var(--line-color);
	}

	.space-between {
		margin: 0 15rem;
	}
</style>
