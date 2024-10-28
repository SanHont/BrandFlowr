<script>
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';

	let isScrolled = false;

	onMount(() => {
		// Simpler animation timeline
		const tl = gsap.timeline({
			defaults: {
				ease: 'power3.out',
				duration: 0.6
			}
		});

		// Animate the entire header container
		tl.from('.header-container', {
			y: -50,
			opacity: 0
		});

		// Simple fade in for logo, nav items, and language selector
		gsap.from(['.logo-container', '.nav-menu', '.lang-select'], {
			opacity: 0,
			duration: 0.4,
			delay: 0.3,
			stagger: 0.1
		});

		// Header scroll effect
		window.addEventListener('scroll', () => {
			isScrolled = window.scrollY > 50;
			const header = document.querySelector('.header-container');

			if (isScrolled) {
				header.classList.add('scrolled');
			} else {
				header.classList.remove('scrolled');
			}
		});
	});
</script>

<div class="header-wrapper">
	<header>
		<div class="header-container">
			<div class="logo-container">
				<span class="brand-text">BrandFlowr</span>
			</div>

			<nav class="nav-menu">
				<a href="/" class="nav-item">Home</a>
				<a href="/services" class="nav-item">Services</a>
				<a href="/portfolio" class="nav-item">Portfolio</a>
				<a href="/about" class="nav-item">About</a>
				<a href="/contact" class="nav-item contact-btn">Let's Talk</a>
				<div class="lang-select">
					<select>
						<option value="en">EN</option>
						<option value="nl">NL</option>
					</select>
				</div>
			</nav>
		</div>
	</header>
</div>

<style>
	.header-wrapper {
		position: fixed;
		width: 100%;
		top: 0;
		left: 0;
		z-index: 1000;
		padding: 1rem 2rem;
	}

	.header-container {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem 5%;
		background-color: var(--text-color);
		border-radius: 1rem;
		box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
	}

	.logo-container {
		display: flex;
		align-items: center;
		gap: 0.8rem;
	}

	.brand-text {
		font-family: 'Montserrat', sans-serif;
		font-size: 1.6rem;
		font-weight: 700;
		letter-spacing: 0.03rem;
		color: var(--services-text-color);
	}

	.nav-menu {
		display: flex;
		gap: 2.5rem;
		align-items: center;
	}

	.nav-item {
		font-family: 'Montserrat', sans-serif;
		font-weight: 500;
		text-decoration: none;
		color: var(--services-text-color);
		font-size: 1rem;
		padding: 0.5rem 0;
		position: relative;
		transition: all 0.3s ease;
	}

	.nav-item:not(.contact-btn)::after {
		content: '';
		position: absolute;
		bottom: 0;
		left: 50%;
		width: 0;
		height: 2px;
		background-color: var(--background-color);
		transition: all 0.3s ease;
		transform: translateX(-50%);
	}

	.nav-item:not(.contact-btn):hover::after {
		width: 100%;
	}

	.contact-btn {
		background-color: var(--background-color);
		color: var(--text-color);
		padding: 0.8rem 1.8rem;
		border-radius: 2rem;
		font-weight: 600;
		transition: all 0.3s ease;
		border: 2px solid var(--background-color);
	}

	.contact-btn:hover {
		background-color: transparent;
		color: var(--background-color);
		transform: translateY(-2px);
	}

	.lang-select select {
		font-family: 'Montserrat', sans-serif;
		font-weight: 500;
		padding: 0.4rem 0.8rem;
		border: 2px solid var(--background-color);
		border-radius: 2rem;
		background: transparent;
		color: var(--services-text-color);
		cursor: pointer;
		transition: all 0.3s ease;
		outline: none;
		font-size: 0.9rem;
		margin-left: 1rem;
	}

	.lang-select select:hover {
		background-color: var(--background-color);
		color: var(--text-color);
	}

	@media (max-width: 968px) {
		.header-wrapper {
			padding: 0;
		}

		.header-container {
			flex-direction: column;
			gap: 1rem;
			border-radius: 0;
		}

		.nav-menu {
			flex-wrap: wrap;
			justify-content: center;
			gap: 1rem;
			padding: 0.5rem 0;
		}

		.brand-text {
			font-size: 1.4rem;
		}

		.lang-select {
			margin: 0.5rem 0;
		}

		.lang-select select {
			margin-left: 0;
		}
	}

	@media (max-width: 480px) {
		.header-container {
			padding: 1rem 3%;
		}

		.nav-item {
			font-size: 0.9rem;
			padding: 0.5rem 0;
		}

		.brand-text {
			font-size: 1.2rem;
		}

		.contact-btn {
			padding: 0.6rem 1.4rem;
		}

		.lang-select select {
			padding: 0.3rem 0.6rem;
			font-size: 0.8rem;
		}
	}
</style>
