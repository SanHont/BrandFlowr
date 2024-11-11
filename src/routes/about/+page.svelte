<script>
	import Menu from '$lib/components/menu.svelte';
	import Footer from '$lib/components/footer.svelte';
</script>

<Menu />

<main>
	<!-- Digital Garden Layout -->
	<div class="digital-garden">
		<!-- Root Section (Main Hero) -->
		<section class="garden-section root-section">
			<div class="section-content">
				<span class="pre-title">About BrandFlowr</span>
				<h1>
					<span class="title-line">Growing Digital</span>
					<span class="title-line highlight">Excellence</span>
				</h1>
				<p class="hero-description">
					We're a team of creative strategists and digital innovators, dedicated to helping brands
					flourish in the ever-evolving social media landscape.
				</p>
			</div>
		</section>
	</div>
</main>

<Footer />

<style>
	main {
		margin-top: 8rem;
		min-height: 100vh;
		overflow: hidden;
	}

	.digital-garden {
		max-width: 1400px;
		margin: 0 auto;
		padding: 2rem;
		position: relative;
	}

	/* Base Section Styles */
	.garden-section {
		margin: 4rem 0;
		padding: 3rem;
		border-radius: 2rem;
		position: relative;
		background: var(--background-primary);
		opacity: 0.95;
	}

	/* Section Content */
	.section-content {
		position: relative;
		z-index: 2;
	}

	/* Section Types */
	.root-section {
		background: transparent;
		color: var(--text-light);
		text-align: center;
		padding: 0 2rem 2rem 2rem;
		margin-bottom: 5rem;
	}

	/* Typography */
	h1 {
		font-family: 'Montserrat', sans-serif;
		font-size: 4rem;
		margin-bottom: 1.5rem;
		font-weight: 800;
	}

	@media (max-width: 768px) {
		.garden-section {
			margin: 2rem 0;
			width: 100% !important;
			margin-left: 0 !important;
			margin-right: 0 !important;
		}

		h1 {
			font-size: 2.5rem;
		}
	}

	/* Add these styles for the updated hero section */
	.pre-title {
		font-family: 'Montserrat', sans-serif;
		font-weight: 600;
		color: var(--text-light);
		text-transform: uppercase;
		letter-spacing: 2px;
		font-size: 0.9rem;
		margin-bottom: 1rem;
		display: inline-block;
		padding: 0.8rem 1.5rem;
		background: rgba(255, 255, 255, 0.1);
		border-radius: 2rem;
		backdrop-filter: blur(10px);
	}

	.title-line {
		display: block;
		font-family: 'Montserrat', sans-serif;
		font-size: 4.5rem;
		font-weight: 800;
		line-height: 1.1;
		margin-bottom: 0.2rem;
		opacity: 0;
		transform: translateY(20px);
		animation: fadeInUp 0.5s ease forwards;
	}

	.title-line:nth-child(1) {
		animation-delay: 0.2s;
	}
	.title-line:nth-child(2) {
		animation-delay: 0.4s;
	}

	.highlight {
		color: var(--bg-primary);
	}

	.hero-description {
		font-family: 'Montserrat', sans-serif;
		font-size: 1.2rem;
		color: var(--text-light);
		max-width: 700px;
		margin: 1rem auto;
		line-height: 1.6;
		opacity: 0.9;
	}

	@keyframes fadeInUp {
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@media (max-width: 768px) {
		.title-line {
			font-size: 3rem;
		}
	}
</style>
