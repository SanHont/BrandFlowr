<script>
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';

	// Move social media icons data to a separate array
	const floatingIcons = [
		{ class: 'icon-1', icon: 'fa-hashtag', size: '2.2rem', top: '20%', left: '15%', delay: '-2s' },
		{ class: 'icon-2', icon: 'fa-heart', size: '1.8rem', top: '30%', right: '20%', delay: '-4s' },
		{ class: 'icon-3', icon: 'fa-comment', size: '2rem', bottom: '25%', left: '30%', delay: '-6s' },
		{ class: 'icon-4', icon: 'fa-share', size: '1.6rem', top: '15%', right: '35%', delay: '-1s' },
		{
			class: 'icon-5',
			icon: 'fa-camera',
			size: '2.1rem',
			bottom: '20%',
			right: '25%',
			delay: '-3s'
		},
		{
			class: 'icon-6',
			icon: 'fa-thumbs-up',
			size: '1.9rem',
			top: '45%',
			left: '20%',
			delay: '-5s'
		},
		{ class: 'icon-7', icon: 'fa-star', size: '1.7rem', top: '60%', right: '15%', delay: '-2s' }
	];

	// Move shapes data to a separate array
	const shapes = [
		{ class: 'shape-1', size: '150px', top: '-75px', left: '-75px', delay: '0s' },
		{ class: 'shape-2', size: '100px', top: '50%', right: '-50px', delay: '-2s' },
		{ class: 'shape-3', size: '200px', bottom: '-100px', left: '50%', delay: '-4s' },
		{ class: 'shape-4', size: '120px', top: '40%', left: '-60px', delay: '-3s' }
	];

	onMount(() => {
		const tl = gsap.timeline({
			defaults: { ease: 'power3.out' }
		});

		tl.from('.hero-shapes', {
			scale: 0.8,
			opacity: 0,
			duration: 1
		}).from(
			'.hero-content',
			{
				y: 30,
				opacity: 0,
				duration: 1
			},
			'-=0.5'
		);
	});
</script>

<div class="hero-container">
	<section class="hero">
		<div class="hero-shapes">
			{#each shapes as shape}
				<div
					class="shape {shape.class}"
					style="
                        width: {shape.size}; 
                        height: {shape.size}; 
                        top: {shape.top}; 
                        left: {shape.left}; 
                        right: {shape.right}; 
                        bottom: {shape.bottom}; 
                        animation-delay: {shape.delay}"
				></div>
			{/each}

			{#each floatingIcons as icon}
				<div
					class="floating-icon {icon.class}"
					style="
                        font-size: {icon.size}; 
                        top: {icon.top}; 
                        left: {icon.left}; 
                        right: {icon.right}; 
                        bottom: {icon.bottom}; 
                        animation-delay: {icon.delay}"
				>
					<i class="fa-solid {icon.icon}"></i>
				</div>
			{/each}
		</div>
		<div class="hero-content">
			<h1>Transform Your Social Media Presence</h1>
			<p>Expert social media management and content creation that helps your brand bloom</p>
			<div class="cta-buttons">
				<a href="/contact" class="primary-btn">Get Started</a>
				<a href="/portfolio" class="secondary-btn">View Our Work</a>
			</div>
		</div>
	</section>
</div>

<style>
	.hero {
		position: relative;
		overflow: hidden;
		background-color: var(--text-color);
		padding: 4%;
		text-align: center;
		border-radius: 1.5rem;
		margin: 2rem auto 4rem;
		width: 70%;
		max-width: 1200px;
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.hero-container {
		display: flex;
		justify-content: center;
		align-items: center;
		justify-items: center;
		padding: 0 2rem;
	}

	.hero-content {
		position: relative;
		z-index: 1;
		max-width: 700px;
		margin: 0 auto;
		padding: 1rem;
	}

	h1 {
		font-size: 3.5rem;
		color: var(--services-text-color);
		margin-bottom: 1.5rem;
		font-weight: 800;
		line-height: 1.2;
		text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	}

	.hero p {
		font-size: 1.3rem;
		color: var(--services-text-color);
		margin-bottom: 2.5rem;
		line-height: 1.6;
		opacity: 0.9;
	}

	.cta-buttons {
		display: flex;
		gap: 2rem;
		justify-content: center;
		margin-top: 3rem;
	}

	.primary-btn,
	.secondary-btn {
		padding: 1.2rem 3rem;
		border-radius: 3rem;
		font-weight: 600;
		text-decoration: none;
		transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
		letter-spacing: 0.5px;
		position: relative;
		overflow: hidden;
	}

	.primary-btn {
		background-color: var(--background-color);
		color: var(--text-color);
		border: 2px solid var(--background-color);
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
	}

	.secondary-btn {
		background-color: transparent;
		color: var(--services-text-color);
		border: 2px solid var(--background-color);
		backdrop-filter: blur(5px);
	}

	.primary-btn:hover {
		transform: translateY(-3px);
		box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
		background-color: #2a9c76;
	}

	.secondary-btn:hover {
		transform: translateY(-3px);
		box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
		background-color: #34b38b7b;
	}

	.primary-btn:active,
	.secondary-btn:active {
		transform: translateY(-1px);
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
	}

	.primary-btn::after,
	.secondary-btn::after {
		content: '';
		position: absolute;
		top: -50%;
		left: -50%;
		width: 200%;
		height: 200%;
		background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
		transform: rotate(45deg);
		transition: 0.6s;
		opacity: 0;
	}

	.primary-btn:hover::after,
	.secondary-btn:hover::after {
		opacity: 1;
	}

	.hero-shapes {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		pointer-events: none;
	}

	.shape {
		position: absolute;
		border-radius: 50%;
		background: var(--background-color);
		opacity: 0.1;
		animation: float 8s infinite ease-in-out;
		backdrop-filter: blur(2px);
	}

	.floating-icon {
		position: absolute;
		color: var(--background-color);
		opacity: 0.15;
		animation: floatIcon 6s infinite ease-in-out;
		filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.1));
	}

	@keyframes float {
		0%,
		100% {
			transform: translateY(0) rotate(0deg);
		}
		50% {
			transform: translateY(20px) rotate(10deg);
		}
	}

	@keyframes floatIcon {
		0%,
		100% {
			transform: translateY(0) scale(1);
		}
		50% {
			transform: translateY(-15px) scale(1.1);
		}
	}

	@media (max-width: 968px) {
		h1 {
			font-size: 2.5rem;
		}

		.cta-buttons {
			flex-direction: column;
			align-items: center;
			gap: 1rem;
		}

		.primary-btn,
		.secondary-btn {
			width: 100%;
			max-width: 300px;
			text-align: center;
			padding: 1rem 2rem;
		}

		.hero {
			width: 85%;
			padding: 8% 4%;
		}
	}

	@media (max-width: 480px) {
		h1 {
			font-size: 2rem;
		}

		.hero p {
			font-size: 1rem;
		}

		.hero {
			width: 90%;
		}

		.hero-container {
			padding: 0 1rem;
		}

		.shape {
			display: none;
		}

		.floating-icon {
			font-size: 1.5rem;
		}
	}
</style>
