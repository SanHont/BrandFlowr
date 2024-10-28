<script>
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { inview } from 'svelte-inview';

	// Move animation configuration to a separate constant
	const ANIMATION_CONFIG = {
		defaults: { ease: 'power3.out' }
	};

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

	// Add counter animation function
	function animateValue(start, end, duration, element) {
		let startTimestamp = null;
		const step = (timestamp) => {
			if (!startTimestamp) startTimestamp = timestamp;
			const progress = Math.min((timestamp - startTimestamp) / duration, 1);
			const value = Math.floor(progress * (end - start) + start);
			element.innerHTML = value + (end === 1000 ? '+' : end === 100000 ? 'K+' : '+');
			if (progress < 1) {
				window.requestAnimationFrame(step);
			}
		};
		window.requestAnimationFrame(step);
	}

	// Add stats data
	const stats = [
		{ number: 50, label: 'Happy Clients', icon: 'fa-users' },
		{ number: 1000, label: 'Posts Created', icon: 'fa-image' },
		{ number: 100000, label: 'Engagement Generated', icon: 'fa-heart' }
	];

	// Add handler for inview
	const handleChange = ({ detail }) => {
		if (detail.inView) {
			stats.forEach((stat, index) => {
				const element = document.querySelector(`#stat-${index}`);
				if (element) {
					animateValue(0, stat.number, 2000, element);
				}
			});
		}
	};

	onMount(() => {
		const tl = gsap.timeline(ANIMATION_CONFIG);

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

	// Add services data
	const services = [
		{
			icon: 'fa-mobile-screen-button',
			title: 'Social Media Management',
			description:
				'Full-service management of your social media presence across all major platforms.',
			color: '#34b38a'
		},
		{
			icon: 'fa-camera',
			title: 'Content Creation',
			description: 'Eye-catching visuals and engaging copy that resonates with your audience.',
			color: '#4ecca3'
		},
		{
			icon: 'fa-chart-line',
			title: 'Strategy & Analytics',
			description: 'Data-driven strategies to grow your online presence and engage your audience.',
			color: '#76d7b8'
		}
	];

	// Add benefits data
	const benefits = [
		{
			icon: 'fa-bullseye',
			title: 'Strategic Approach',
			description:
				'We create tailored social media strategies that align with your business goals and target audience.'
		},
		{
			icon: 'fa-lightbulb',
			title: 'Creative Excellence',
			description:
				'Our team delivers unique, engaging content that makes your brand stand out in the digital space.'
		},
		{
			icon: 'fa-arrow-trend-up',
			title: 'Proven Results',
			description: 'Track your growth with detailed analytics and see real engagement improvements.'
		},
		{
			icon: 'fa-handshake',
			title: 'Personal Touch',
			description:
				'We work closely with you to ensure your brands voice and values shine through in every post.'
		}
	];

	// Add process data
	const processSteps = [
		{
			icon: 'fa-magnifying-glass',
			title: 'Discovery',
			description:
				'We learn about your brand, goals, and target audience to create a tailored strategy.'
		},
		{
			icon: 'fa-chess',
			title: 'Strategy',
			description:
				'Develop a comprehensive social media plan aligned with your business objectives.'
		},
		{
			icon: 'fa-pen-to-square',
			title: 'Creation',
			description:
				'Produce engaging content that resonates with your audience and reflects your brand.'
		},
		{
			icon: 'fa-rocket',
			title: 'Growth',
			description:
				'Monitor performance, engage with your audience, and optimize for better results.'
		}
	];
</script>

<main>
	<!-- Hero Section -->
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

	<!-- Stats Section -->
	<section class="stats" use:inview={{ unobserveOnEnter: true }} on:change={handleChange}>
		<div class="stats-container">
			{#each stats as stat, index}
				<div class="stat-item" style="--delay: {index * 0.2}s">
					<div class="stat-icon">
						<i class="fa-solid {stat.icon}"></i>
					</div>
					<div class="stat-content">
						<h3 id="stat-{index}">0{stat.number === 100000 ? 'K+' : '+'}</h3>
						<p>{stat.label}</p>
					</div>
					<div class="stat-background"></div>
				</div>
			{/each}
		</div>
	</section>

	<!-- Featured Services -->
	<section class="featured-services" use:inview={{ unobserveOnEnter: true }}>
		<h2>Our Services</h2>
		<div class="services-grid">
			{#each services as service, index}
				<div class="service-card" style="--delay: {index * 0.2}s; --accent-color: {service.color}">
					<div class="service-icon">
						<i class="fa-solid {service.icon}"></i>
						<div class="icon-background"></div>
					</div>
					<h3>{service.title}</h3>
					<p>{service.description}</p>
					<div class="service-hover">
						<span class="learn-more">Learn More →</span>
					</div>
				</div>
			{/each}
		</div>
	</section>

	<!-- Why Choose Us Section -->
	<section class="why-choose-us" use:inview={{ unobserveOnEnter: true }}>
		<div class="section-header">
			<h2>Why Choose BrandFlowr?</h2>
			<div class="header-line"></div>
		</div>
		<div class="benefits-grid">
			{#each benefits as benefit, index}
				<div class="benefit-card" style="--delay: {index * 0.15}s">
					<div class="benefit-icon-wrapper">
						<i class="fa-solid {benefit.icon}"></i>
						<div class="icon-ring"></div>
					</div>
					<div class="benefit-content">
						<h3>{benefit.title}</h3>
						<p>{benefit.description}</p>
					</div>
					<div class="card-background"></div>
				</div>
			{/each}
		</div>
	</section>

	<!-- Process Section -->
	<section class="process" use:inview={{ unobserveOnEnter: true }}>
		<div class="section-header">
			<h2>Our Process</h2>
			<div class="header-line"></div>
		</div>
		<div class="process-container">
			<div class="process-center-line"></div>
			<div class="process-steps">
				{#each processSteps as step, index}
					<div
						class="process-card {index % 2 === 0 ? 'left' : 'right'}"
						style="--delay: {index * 0.3}s"
					>
						<!-- Update the Process Section's step content -->
						<div class="step-content">
							<div class="step-header">
								<div class="step-icon-container">
									<div class="step-icon-wrapper">
										<i class="fa-solid {step.icon}"></i>
										<div class="icon-ring"></div>
										<div class="icon-pulse"></div>
									</div>
									<div class="step-number">Step {index + 1}</div>
								</div>
							</div>
							<div class="step-details">
								<h3>{step.title}</h3>
								<p>{step.description}</p>
							</div>
							<div class="step-connector">
								<div class="connector-dot"></div>
								<div class="connector-line">
									<div class="line-progress"></div>
								</div>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<!-- Testimonials Section -->
	<section class="testimonials" use:inview={{ unobserveOnEnter: true }}>
		<div class="section-header">
			<h2>What Our Clients Say</h2>
			<p class="section-subtext">Real feedback from businesses we've helped grow</p>
			<div class="header-line"></div>
		</div>
		<div class="testimonials-grid">
			<div class="testimonial-card" style="--delay: 0.2s">
				<div class="testimonial-icon">
					<i class="fa-solid fa-quote-left"></i>
					<div class="icon-ring"></div>
				</div>
				<div class="rating">
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
				</div>
				<p>
					BrandFlowr transformed our social media presence. Their creative approach and strategic
					thinking helped us connect with our audience in ways we never imagined. Our engagement
					rates have increased by 300% since working with them.
				</p>
				<div class="client-info">
					<div class="client-profile">
						<div class="client-image">
							<img
								src="https://ui-avatars.com/api/?name=Sarah+Johnson&background=34b38a&color=fff"
								alt="Sarah Johnson"
							/>
							<div class="client-status">
								<i class="fa-solid fa-check"></i>
							</div>
						</div>
						<div class="client-details">
							<strong>Sarah Johnson</strong>
							<span>Marketing Director at TechStart Solutions</span>
						</div>
					</div>
				</div>
			</div>

			<div class="testimonial-card" style="--delay: 0.4s">
				<div class="testimonial-icon">
					<i class="fa-solid fa-quote-left"></i>
					<div class="icon-ring"></div>
				</div>
				<div class="rating">
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
				</div>
				<p>
					Professional, creative, and results-driven. The team at BrandFlowr consistently delivers
					content that engages our followers and drives real business results. They've helped us
					double our social media following in just 6 months.
				</p>
				<div class="client-info">
					<div class="client-profile">
						<div class="client-image">
							<img
								src="https://ui-avatars.com/api/?name=Michael+Berg&background=34b38a&color=fff"
								alt="Michael van der Berg"
							/>
							<div class="client-status">
								<i class="fa-solid fa-check"></i>
							</div>
						</div>
						<div class="client-details">
							<strong>Michael van der Berg</strong>
							<span>Business Owner at Artisan Cafe Co.</span>
						</div>
					</div>
				</div>
			</div>

			<div class="testimonial-card" style="--delay: 0.6s">
				<div class="testimonial-icon">
					<i class="fa-solid fa-quote-left"></i>
					<div class="icon-ring"></div>
				</div>
				<div class="rating">
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
					<i class="fa-solid fa-star"></i>
				</div>
				<p>
					Working with BrandFlowr has been a game-changer for our brand. Their attention to detail
					and understanding of our industry is exceptional. They've helped us build a strong
					community around our brand and increase our online sales.
				</p>
				<div class="client-info">
					<div class="client-profile">
						<div class="client-image">
							<img
								src="https://ui-avatars.com/api/?name=Emma+Davis&background=34b38a&color=fff"
								alt="Emma Davis"
							/>
							<div class="client-status">
								<i class="fa-solid fa-check"></i>
							</div>
						</div>
						<div class="client-details">
							<strong>Emma Davis</strong>
							<span>CEO at Eco Lifestyle Brands</span>
						</div>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- CTA Section -->
	<section class="cta-section">
		<div class="cta-content">
			<h2>Ready to Grow Your Brand?</h2>
			<p>Let's create a social media strategy that works for your business.</p>
			<a href="/contact" class="cta-button">Schedule a Free Consultation</a>
		</div>
	</section>
</main>

<style>
	main {
		font-family: 'Montserrat', sans-serif;
		margin-top: 8rem; /* Space for fixed header */
	}

	.hero {
		position: relative;
		overflow: hidden;
		background-color: var(--text-color); /* Single solid color */
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
		padding: 0 2rem; /* Added padding */
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
		font-weight: 800; /* Increased weight */
		line-height: 1.2; /* Added line height */
		text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Subtle text shadow */
	}

	.hero p {
		font-size: 1.3rem; /* Slightly larger */
		color: var(--services-text-color);
		margin-bottom: 2.5rem; /* Increased spacing */
		line-height: 1.6;
		opacity: 0.9;
	}

	.cta-buttons {
		display: flex;
		gap: 2rem; /* Increased from 1.5rem */
		justify-content: center;
		margin-top: 3rem; /* Added more space above buttons */
	}

	.primary-btn,
	.secondary-btn {
		padding: 1.2rem 3rem; /* Increased horizontal padding */
		border-radius: 3rem; /* Slightly more rounded */
		font-weight: 600;
		text-decoration: none;
		transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1); /* Smoother animation */
		letter-spacing: 0.5px;
		position: relative; /* For pseudo-element */
		overflow: hidden; /* For hover effect */
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
		backdrop-filter: blur(5px); /* Adds depth */
	}

	/* Enhanced hover effects */
	.primary-btn:hover {
		transform: translateY(-3px);
		box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
		background-color: #2a9c76; /* Slightly darker shade */
	}

	.secondary-btn:hover {
		transform: translateY(-3px);
		box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
		background-color: #34b38b7b;
	}

	/* Active state for better interaction feedback */
	.primary-btn:active,
	.secondary-btn:active {
		transform: translateY(-1px);
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
	}

	/* Add subtle shine effect on hover */
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

	/* Stats Section */
	.stats {
		padding: 4%;
		background-color: var(--services-background-color);
		position: relative;
		overflow: hidden;
	}

	.stats-container {
		display: flex;
		justify-content: space-around;
		max-width: 1200px;
		margin: 0 auto;
		gap: 2rem;
	}

	.stat-item {
		position: relative;
		text-align: center;
		color: var(--text-color);
		padding: 1.5rem;
		width: 28%;
		border-radius: 1rem;
		background: rgba(255, 255, 255, 0.1);
		backdrop-filter: blur(10px);
		transition: transform 0.3s ease;
		animation: fadeInUp 0.6s ease forwards;
		animation-delay: var(--delay);
		opacity: 0;
	}

	.stat-icon {
		font-size: 2.5rem;
		margin-bottom: 1rem;
		color: var(--text-color);
		opacity: 0.9;
	}

	.stat-content {
		position: relative;
		z-index: 1;
	}

	.stat-background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(
			135deg,
			rgba(255, 255, 255, 0.1) 0%,
			rgba(255, 255, 255, 0.05) 100%
		);
		border-radius: 1rem;
		transition: transform 0.3s ease;
	}

	.stat-item:hover {
		transform: translateY(-5px);
	}

	.stat-item:hover .stat-background {
		transform: scale(1.05);
	}

	.stat-item h3 {
		font-size: 2.8rem;
		margin-bottom: 0.5rem;
		font-weight: 700;
		background: linear-gradient(135deg, var(--text-color) 0%, #ffffff 100%);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
	}

	.stat-item p {
		font-size: 1.1rem;
		opacity: 0.9;
		font-weight: 500;
	}

	@keyframes fadeInUp {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	/* Featured Services */
	.featured-services {
		padding: 4%;
		background-color: var(--text-color);
		position: relative;
		overflow: hidden;
	}

	.featured-services h2 {
		text-align: center;
		color: var(--services-text-color);
		margin-bottom: 4rem;
		font-size: 2.8rem;
		position: relative;
		display: inline-block;
		left: 50%;
		transform: translateX(-50%);
	}

	.featured-services h2::after {
		content: '';
		position: absolute;
		bottom: -10px;
		left: 50%;
		transform: translateX(-50%);
		width: 50%;
		height: 3px;
		background: var(--background-color);
		border-radius: 2px;
	}

	.services-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
		gap: 2.5rem;
		max-width: 1200px;
		margin: 0 auto;
		padding: 1rem;
	}

	.service-card {
		background-color: white;
		padding: 2.5rem;
		border-radius: 1.5rem;
		text-align: center;
		position: relative;
		transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.05);
		animation: fadeInUp 0.6s ease forwards;
		animation-delay: var(--delay);
		opacity: 0;
		cursor: pointer;
	}

	.service-icon {
		position: relative;
		width: 80px;
		height: 80px;
		margin: 0 auto 1.5rem;
	}

	.service-icon i {
		font-size: 2.2rem;
		color: var(--accent-color);
		position: relative;
		z-index: 2;
		line-height: 80px;
	}

	.icon-background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: var(--accent-color);
		opacity: 0.1;
		border-radius: 1rem;
		transform: rotate(45deg);
		transition: all 0.3s ease;
	}

	.service-card h3 {
		color: var(--services-text-color);
		margin-bottom: 1rem;
		font-size: 1.6rem;
		font-weight: 700;
		transition: color 0.3s ease;
	}

	.service-card p {
		color: var(--services-text-color);
		opacity: 0.8;
		line-height: 1.7;
		margin-bottom: 1.5rem;
		transition: opacity 0.3s ease;
	}

	.service-hover {
		position: absolute;
		bottom: 0;
		left: 0;
		width: 100%;
		padding: 1.5rem;
		background: linear-gradient(to top, rgba(255, 255, 255, 1) 0%, rgba(255, 255, 255, 0) 100%);
		opacity: 0;
		transition: all 0.3s ease;
	}

	.learn-more {
		color: var(--accent-color);
		font-weight: 600;
		font-size: 1.1rem;
	}

	/* Hover effects */
	.service-card:hover {
		transform: translateY(-10px);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.service-card:hover .icon-background {
		transform: rotate(90deg) scale(1.1);
		opacity: 0.15;
	}

	.service-card:hover .service-hover {
		opacity: 1;
	}

	@media (max-width: 768px) {
		.services-grid {
			grid-template-columns: 1fr;
			padding: 0.5rem;
		}

		.service-card {
			padding: 2rem;
		}

		.featured-services h2 {
			font-size: 2.2rem;
		}
	}

	/* Add these styles after your existing styles */

	.why-choose-us {
		padding: 4%;
		background-color: var(--services-background-color);
		position: relative;
		overflow: hidden;
	}

	.section-header {
		text-align: center;
		position: relative;
	}

	.section-header h2 {
		color: var(--text-color);
		font-size: 2.8rem;
		margin-bottom: 1rem;
		position: relative;
		display: inline-block;
	}

	.header-line {
		width: 80px;
		height: 4px;
		background: var(--text-color);
		margin: 1rem auto;
		border-radius: 2px;
		position: relative;
	}

	.header-line::before,
	.header-line::after {
		content: '';
		position: absolute;
		width: 40px;
		height: 4px;
		background: var(--text-color);
		border-radius: 2px;
		opacity: 0.5;
	}

	.header-line::before {
		left: -50px;
	}

	.header-line::after {
		right: -50px;
	}

	.benefits-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr); /* 2x2 grid */
		gap: 2.5rem;
		max-width: 1200px;
		margin: 0 auto;
		padding: 1rem;
	}

	.benefit-card {
		background-color: var(--text-color);
		padding: 2.5rem;
		border-radius: 1.5rem;
		position: relative;
		transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
		overflow: hidden;
		animation: fadeInUp 0.6s ease forwards;
		animation-delay: var(--delay);
		opacity: 0;
		display: flex; /* Added flex display */
		gap: 1.5rem; /* Space between icon and content */
		align-items: flex-start; /* Align items to top */
	}

	.benefit-icon-wrapper {
		flex-shrink: 0; /* Prevent icon from shrinking */
		position: relative;
		width: 60px;
		height: 60px;
		margin: 0;
		display: flex; /* Added */
		align-items: center; /* Added */
		justify-content: center; /* Added */
	}

	.benefit-icon-wrapper i {
		font-size: 1.8rem;
		color: var(--background-color);
		position: relative;
		z-index: 2;
		line-height: 1; /* Changed from line-height: 60px */
		transition: transform 0.3s ease;
	}

	.benefit-content {
		flex: 1;
		text-align: left;
	}

	.benefit-card h3 {
		color: var(--services-text-color);
		font-size: 1.5rem;
		margin-bottom: 0.8rem;
		font-weight: 700;
		text-align: left;
	}

	.benefit-card p {
		color: var(--services-text-color);
		opacity: 0.8;
		line-height: 1.6;
		font-size: 1rem;
		text-align: left;
	}

	/* Keep existing hover effects and animations */
	.benefit-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.benefit-card:hover .icon-ring {
		transform: translate(-50%, -50%) scale(1.1) rotate(45deg); /* Updated */
		opacity: 0.4;
	}

	.benefit-card:hover .icon-ring::after {
		transform: translate(-50%, -50%) scale(1.2) rotate(-45deg); /* Updated */
		opacity: 0.2;
	}

	.benefit-card:hover .card-background {
		opacity: 1;
	}

	/* Add animation for icon */
	.benefit-icon-wrapper i {
		font-size: 1.8rem;
		color: var(--background-color);
		position: relative;
		z-index: 2;
		line-height: 60px;
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-icon-wrapper i {
		transform: scale(1.1);
	}

	/* Add a subtle transition for text */
	.benefit-content h3,
	.benefit-content p {
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-content h3 {
		transform: translateY(-2px);
	}

	.benefit-card:hover .benefit-content p {
		transform: translateY(-1px);
	}

	/* Update media query */
	@media (max-width: 968px) {
		.benefits-grid {
			grid-template-columns: 1fr; /* Single column on mobile */
			max-width: 600px;
		}

		.benefit-card {
			padding: 2rem;
		}
	}

	.process {
		padding: 4%;
		background-color: var(--text-color);
		position: relative;
		overflow: hidden;
	}

	.process h2 {
		color: var(--services-text-color);
	}

	.process-container {
		max-width: 1200px;
		margin: 0 auto 0;
		padding: 2rem;
		position: relative;
	}

	.process-center-line {
		position: absolute;
		left: 50%;
		top: 0;
		bottom: 0;
		width: 4px;
		background: linear-gradient(
			to bottom,
			transparent,
			var(--background-color) 10%,
			var(--background-color) 90%,
			transparent
		);
		opacity: 0.3;
		transform: translateX(-50%);
	}

	.process-steps {
		position: relative;
		display: flex;
		flex-direction: column;
		gap: 4rem;
	}

	.process-card {
		width: 42%; /* Reduced from 45% */
		position: relative;
		animation: slideIn 0.8s ease forwards;
		animation-delay: var(--delay);
		opacity: 0;
	}

	.process-card.left {
		align-self: flex-start;
		transform: translateX(-30px);
	}

	.process-card.right {
		align-self: flex-end;
		transform: translateX(30px);
	}

	.step-content {
		background: white;
		padding: 2rem; /* Reduced from 2.5rem */
		border-radius: 1.5rem;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
		transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
		position: relative;
	}

	.step-header {
		display: flex;
		align-items: center;
		gap: 1.5rem;
		margin-bottom: 1.5rem;
	}

	.step-icon-container {
		position: relative;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 0.5rem;
	}

	.step-icon-wrapper {
		position: relative;
		width: 60px; /* Reduced from 70px */
		height: 60px; /* Reduced from 70px */
		display: flex;
		align-items: center;
		justify-content: center;
		background: rgba(52, 179, 138, 0.1);
		border-radius: 50%; /* Changed from 1rem to make it circular */
		transition: all 0.4s ease;
	}

	.step-icon-wrapper i {
		font-size: 2rem;
		color: var(--background-color);
		position: relative;
		z-index: 2;
		transition: all 0.4s ease;
	}

	.icon-ring {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border: 2px solid var(--background-color);
		border-radius: 50%; /* Changed from 1rem to match circular shape */
		opacity: 0.2;
		transition: all 0.4s ease;
	}

	.icon-pulse {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border-radius: 50%; /* Changed from 1rem to match circular shape */
		background: var(--background-color);
		opacity: 0;
		animation: pulseCircle 2s infinite;
	}

	.line-progress {
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
		background: var(--background-color);
		width: 0;
		transition: width 0.6s ease;
	}

	.step-details h3 {
		color: var(--services-text-color);
		font-size: 1.6rem;
		margin-bottom: 1rem;
	}

	.step-details p {
		color: var(--services-text-color);
		opacity: 0.8;
		line-height: 1.6;
	}

	.step-connector {
		position: absolute;
		top: 50%;
		width: 50px;
		height: 2px;
		display: flex; /* Added */
		align-items: center; /* Added */
	}

	.left .step-connector {
		right: -50px;
	}

	.right .step-connector {
		left: -50px;
	}

	.connector-dot {
		position: absolute;
		width: 12px;
		height: 12px;
		background: var(--background-color);
		border-radius: 50%;
		z-index: 2;
		transition: all 0.4s ease;
		top: 50%; /* Changed */
		transform: translateY(-50%); /* Added */
	}

	.left .connector-dot {
		right: -10px;
	}

	.right .connector-dot {
		left: -10px;
	}

	.connector-line {
		position: relative;
		height: 3px; /* Match this with the dot size */
		background: linear-gradient(to right, rgba(52, 179, 138, 0.2), rgba(52, 179, 138, 0.4));
		width: 100%;
	}

	.step-number {
		font-weight: 700;
		color: var(--background-color);
		font-size: 1rem;
		letter-spacing: 0.5px;
		opacity: 0.8;
		transition: all 0.4s ease;
	}

	@keyframes slideIn {
		from {
			opacity: 0;
			transform: translateX(var(--slide-distance)) scale(0.95);
		}
		to {
			opacity: 1;
			transform: translateX(0) scale(1);
		}
	}

	.process-card.left {
		--slide-distance: -30px;
	}

	.process-card.right {
		--slide-distance: 30px;
	}

	/* Hover effects */
	.step-content:hover {
		transform: translateY(-5px) scale(1.02);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.12);
	}

	.step-content:hover .step-icon-wrapper {
		transform: scale(1.1);
		background: rgba(52, 179, 138, 0.15);
	}

	/* Add new keyframes */
	@keyframes pulseCircle {
		0% {
			transform: translate(-50%, -50%) scale(0.95);
			opacity: 0.3;
		}
		50% {
			transform: translate(-50%, -50%) scale(1.2);
			opacity: 0;
		}
		100% {
			transform: translate(-50%, -50%) scale(0.95);
			opacity: 0.3;
		}
	}

	/* Update connector styles for smoother look */
	.connector-line {
		height: 3px; /* Slightly thicker */
		background: linear-gradient(to right, rgba(52, 179, 138, 0.2), rgba(52, 179, 138, 0.4));
	}

	/* Update mobile styles */
	@media (max-width: 768px) {
		.process-card {
			width: calc(100% - 50px); /* Slightly reduced width */
			margin-left: 50px;
		}

		.step-content {
			padding: 1.5rem;
		}
	}

	/* Update step number style */
	.step-number {
		font-weight: 700;
		color: var(--background-color);
		font-size: 1rem;
		letter-spacing: 0.5px;
		opacity: 0.8;
		transition: all 0.4s ease;
	}

	.step-content:hover .step-number {
		transform: scale(1.1);
		opacity: 1;
	}

	/* Mobile responsive */
	@media (max-width: 768px) {
		.process-center-line {
			left: 30px;
		}

		.process-card {
			width: calc(100% - 60px);
			margin-left: 60px;
		}

		.process-card.left,
		.process-card.right {
			align-self: flex-start;
		}

		.step-connector {
			left: -50px !important;
			width: 50px !important;
		}

		.connector-dot {
			left: -56px !important;
		}
	}

	.testimonials {
		padding: 4%;
		background-color: var(--services-background-color);
		color: var(--text-color);
	}

	.testimonials-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
		gap: 2rem;
		max-width: 1200px;
		margin: 3rem auto 0;
	}

	.testimonial-card {
		background-color: var(--text-color);
		padding: 2rem;
		border-radius: 1rem;
		position: relative;
	}

	.quote {
		font-size: 4rem;
		position: absolute;
		top: -1rem;
		left: 1rem;
		color: var(--background-color);
		opacity: 0.3;
	}

	.client-info {
		margin-top: 1.5rem;
		display: flex;
		flex-direction: column;
		gap: 0.25rem;
	}

	.cta-section {
		padding: 6rem 5%;
		background-color: var(--text-color);
		text-align: center;
	}

	.cta-content {
		max-width: 800px;
		margin: 0 auto;
	}

	.cta-button {
		display: inline-block;
		background-color: var(--background-color);
		color: var(--text-color);
		padding: 1rem 2rem;
		border-radius: 2rem;
		font-weight: 600;
		text-decoration: none;
		margin-top: 2rem;
		transition: transform 0.3s ease;
	}

	.cta-button:hover {
		transform: translateY(-2px);
	}

	@media (max-width: 968px) {
		h1 {
			font-size: 2.5rem;
		}

		.stats-container {
			flex-direction: column;
			align-items: center;
		}

		.cta-buttons {
			flex-direction: column;
			align-items: center;
			gap: 1rem; /* Reduced gap for mobile */
		}

		.primary-btn,
		.secondary-btn {
			width: 100%; /* Full width on mobile */
			max-width: 300px; /* Maximum width to maintain readability */
			text-align: center;
			padding: 1rem 2rem; /* Slightly smaller padding on mobile */
		}

		.hero {
			width: 85%; /* Adjusted for mobile */
			padding: 8% 4%;
		}

		.stat-item {
			width: 100%;
			max-width: 350px;
		}
	}

	@media (max-width: 480px) {
		h1 {
			font-size: 2rem;
		}

		.hero p {
			font-size: 1rem;
		}

		.service-card {
			padding: 1.5rem;
		}

		.hero {
			width: 90%; /* Further adjusted for smaller screens */
		}

		.hero-container {
			padding: 0 1rem;
		}
	}

	@media (max-width: 768px) {
		.benefits-grid,
		.process-steps,
		.testimonials-grid {
			grid-template-columns: 1fr;
		}

		.step::after {
			display: none;
		}

		.shape {
			display: none;
		}

		.floating-icon {
			font-size: 1.5rem;
		}
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

	/* Add these styles to your existing Why Choose Us section styles */

	.icon-ring {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.2;
		transition: all 0.3s ease;
	}

	.icon-ring::after {
		content: '';
		position: absolute;
		top: -5px;
		left: -5px;
		right: -5px;
		bottom: -5px;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.1;
		transition: all 0.3s ease;
	}

	.card-background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(135deg, rgba(52, 179, 138, 0.05) 0%, rgba(52, 179, 138, 0.02) 100%);
		opacity: 0;
		transition: opacity 0.3s ease;
		border-radius: 1.5rem;
	}

	/* Enhanced hover effects */
	.benefit-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.benefit-card:hover .icon-ring {
		transform: scale(1.1) rotate(45deg);
		opacity: 0.4;
	}

	.benefit-card:hover .icon-ring::after {
		transform: scale(1.2) rotate(-45deg);
		opacity: 0.2;
	}

	.benefit-card:hover .card-background {
		opacity: 1;
	}

	/* Add animation for icon */
	.benefit-icon-wrapper i {
		font-size: 1.8rem;
		color: var(--background-color);
		position: relative;
		z-index: 2;
		line-height: 60px;
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-icon-wrapper i {
		transform: scale(1.1);
	}

	/* Add a subtle transition for text */
	.benefit-content h3,
	.benefit-content p {
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-content h3 {
		transform: translateY(-2px);
	}

	.benefit-card:hover .benefit-content p {
		transform: translateY(-1px);
	}

	/* Update the icon ring styles */
	.icon-ring {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.2;
		transition: all 0.3s ease;
	}

	.icon-ring::after {
		content: '';
		position: absolute;
		top: -8px;
		left: -8px;
		right: -8px;
		bottom: -8px;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.1;
		transition: all 0.3s ease;
	}

	/* Update hover animations to keep position fixed */
	.benefit-card:hover .icon-ring {
		opacity: 0.5;
		transform: translate(-50%, -50%) rotate(45deg);
	}

	.benefit-card:hover .icon-ring::after {
		opacity: 0.3;
		transform: rotate(-45deg);
	}

	/* Update step number style */
	.step-number {
		font-weight: 700;
		color: var(--background-color);
		font-size: 1rem;
		letter-spacing: 0.5px;
		opacity: 0.8;
		transition: all 0.4s ease;
	}

	.step-content:hover .step-number {
		transform: scale(1.1);
		opacity: 1;
	}

	/* Mobile responsive */
	@media (max-width: 768px) {
		.process-center-line {
			left: 30px;
		}

		.process-card {
			width: calc(100% - 60px);
			margin-left: 60px;
		}

		.process-card.left,
		.process-card.right {
			align-self: flex-start;
		}

		.step-connector {
			left: -50px !important;
			width: 50px !important;
		}

		.connector-dot {
			left: -56px !important;
		}
	}

	.testimonials {
		padding: 6rem 5%;
		background-color: var(--services-background-color);
		color: var(--text-color);
	}

	.testimonials-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
		gap: 2rem;
		max-width: 1200px;
		margin: 3rem auto 0;
	}

	.testimonial-card {
		background-color: var(--text-color);
		padding: 2rem;
		border-radius: 1rem;
		position: relative;
	}

	.quote {
		font-size: 4rem;
		position: absolute;
		top: -1rem;
		left: 1rem;
		color: var(--background-color);
		opacity: 0.3;
	}

	.client-info {
		margin-top: 1.5rem;
		display: flex;
		flex-direction: column;
		gap: 0.25rem;
	}

	.cta-section {
		padding: 6rem 5%;
		background-color: var(--text-color);
		text-align: center;
	}

	.cta-content {
		max-width: 800px;
		margin: 0 auto;
	}

	.cta-button {
		display: inline-block;
		background-color: var(--background-color);
		color: var(--text-color);
		padding: 1rem 2rem;
		border-radius: 2rem;
		font-weight: 600;
		text-decoration: none;
		margin-top: 2rem;
		transition: transform 0.3s ease;
	}

	.cta-button:hover {
		transform: translateY(-2px);
	}

	@media (max-width: 968px) {
		h1 {
			font-size: 2.5rem;
		}

		.stats-container {
			flex-direction: column;
			align-items: center;
		}

		.cta-buttons {
			flex-direction: column;
			align-items: center;
			gap: 1rem; /* Reduced gap for mobile */
		}

		.primary-btn,
		.secondary-btn {
			width: 100%; /* Full width on mobile */
			max-width: 300px; /* Maximum width to maintain readability */
			text-align: center;
			padding: 1rem 2rem; /* Slightly smaller padding on mobile */
		}

		.hero {
			width: 85%; /* Adjusted for mobile */
			padding: 8% 4%;
		}

		.stat-item {
			width: 100%;
			max-width: 350px;
		}
	}

	@media (max-width: 480px) {
		h1 {
			font-size: 2rem;
		}

		.hero p {
			font-size: 1rem;
		}

		.service-card {
			padding: 1.5rem;
		}

		.hero {
			width: 90%; /* Further adjusted for smaller screens */
		}

		.hero-container {
			padding: 0 1rem;
		}
	}

	@media (max-width: 768px) {
		.benefits-grid,
		.process-steps,
		.testimonials-grid {
			grid-template-columns: 1fr;
		}

		.step::after {
			display: none;
		}

		.shape {
			display: none;
		}

		.floating-icon {
			font-size: 1.5rem;
		}
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

	/* Add these styles to your existing Why Choose Us section styles */

	.icon-ring {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.2;
		transition: all 0.3s ease;
	}

	.icon-ring::after {
		content: '';
		position: absolute;
		top: -5px;
		left: -5px;
		right: -5px;
		bottom: -5px;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.1;
		transition: all 0.3s ease;
	}

	.card-background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(135deg, rgba(52, 179, 138, 0.05) 0%, rgba(52, 179, 138, 0.02) 100%);
		opacity: 0;
		transition: opacity 0.3s ease;
		border-radius: 1.5rem;
	}

	/* Enhanced hover effects */
	.benefit-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.benefit-card:hover .icon-ring {
		transform: scale(1.1) rotate(45deg);
		opacity: 0.4;
	}

	.benefit-card:hover .icon-ring::after {
		transform: scale(1.2) rotate(-45deg);
		opacity: 0.2;
	}

	.benefit-card:hover .card-background {
		opacity: 1;
	}

	/* Add animation for icon */
	.benefit-icon-wrapper i {
		font-size: 1.8rem;
		color: var(--background-color);
		position: relative;
		z-index: 2;
		line-height: 60px;
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-icon-wrapper i {
		transform: scale(1.1);
	}

	/* Add a subtle transition for text */
	.benefit-content h3,
	.benefit-content p {
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-content h3 {
		transform: translateY(-2px);
	}

	.benefit-card:hover .benefit-content p {
		transform: translateY(-1px);
	}

	/* Update the icon ring styles */
	.icon-ring {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.2;
		transition: all 0.3s ease;
	}

	.icon-ring::after {
		content: '';
		position: absolute;
		top: -8px;
		left: -8px;
		right: -8px;
		bottom: -8px;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.1;
		transition: all 0.3s ease;
	}

	/* Update hover animations to keep position fixed */
	.benefit-card:hover .icon-ring {
		opacity: 0.5;
		transform: translate(-50%, -50%) rotate(45deg);
	}

	.benefit-card:hover .icon-ring::after {
		opacity: 0.3;
		transform: rotate(-45deg);
	}

	/* Update Testimonials styles */
	.testimonials {
		padding: 6rem 5%;
		background-color: var(--services-background-color);
		position: relative;
		overflow: hidden;
	}

	.testimonials-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 2.5rem;
		max-width: 1200px;
		margin: 4rem auto 0;
		padding: 1rem;
		position: relative;
	}

	.testimonial-card {
		background-color: var(--text-color);
		padding: 3rem 2rem 2rem;
		border-radius: 1.5rem;
		position: relative;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
		transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
		animation: fadeInUp 0.8s ease forwards;
		animation-delay: var(--delay);
		opacity: 0;
		display: flex;
		flex-direction: column;
		height: 100%;
	}

	.testimonial-icon {
		position: absolute;
		top: -30px;
		left: 50%;
		transform: translateX(-50%);
		width: 60px;
		height: 60px;
		background: var(--services-background-color);
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
	}

	.testimonial-icon i {
		font-size: 1.8rem;
		color: var(--text-color);
		position: relative;
		z-index: 2;
		transition: transform 0.3s ease;
	}

	.rating {
		color: #ffd700;
		margin-bottom: 1.5rem;
		font-size: 1.1rem;
		text-align: center;
	}

	.testimonial-card p {
		color: var(--services-text-color);
		font-size: 1.1rem;
		line-height: 1.7;
		margin-bottom: 2rem;
		position: relative;
		z-index: 1;
		flex-grow: 1;
		text-align: center;
		font-style: italic;
	}

	.client-info {
		border-top: 1px solid rgba(52, 179, 138, 0.1);
		margin-top: auto;
		padding-top: 1.5rem;
		position: relative;
		z-index: 1;
	}

	.client-profile {
		display: flex;
		align-items: center;
		gap: 1rem;
		margin-bottom: 0.8rem;
	}

	.client-image {
		position: relative;
	}

	.cta-button:hover {
		transform: translateY(-2px);
	}

	@media (max-width: 968px) {
		h1 {
			font-size: 2.5rem;
		}

		.stats-container {
			flex-direction: column;
			align-items: center;
		}

		.cta-buttons {
			flex-direction: column;
			align-items: center;
			gap: 1rem; /* Reduced gap for mobile */
		}

		.primary-btn,
		.secondary-btn {
			width: 100%; /* Full width on mobile */
			max-width: 300px; /* Maximum width to maintain readability */
			text-align: center;
			padding: 1rem 2rem; /* Slightly smaller padding on mobile */
		}

		.hero {
			width: 85%; /* Adjusted for mobile */
			padding: 8% 4%;
		}

		.stat-item {
			width: 100%;
			max-width: 350px;
		}
	}

	@media (max-width: 480px) {
		h1 {
			font-size: 2rem;
		}

		.hero p {
			font-size: 1rem;
		}

		.service-card {
			padding: 1.5rem;
		}

		.hero {
			width: 90%; /* Further adjusted for smaller screens */
		}

		.hero-container {
			padding: 0 1rem;
		}
	}

	@media (max-width: 768px) {
		.benefits-grid,
		.process-steps,
		.testimonials-grid {
			grid-template-columns: 1fr;
		}

		.step::after {
			display: none;
		}

		.shape {
			display: none;
		}

		.floating-icon {
			font-size: 1.5rem;
		}
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

	/* Add these styles to your existing Why Choose Us section styles */

	.icon-ring {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.2;
		transition: all 0.3s ease;
	}

	.icon-ring::after {
		content: '';
		position: absolute;
		top: -5px;
		left: -5px;
		right: -5px;
		bottom: -5px;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.1;
		transition: all 0.3s ease;
	}

	.card-background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: linear-gradient(135deg, rgba(52, 179, 138, 0.05) 0%, rgba(52, 179, 138, 0.02) 100%);
		opacity: 0;
		transition: opacity 0.3s ease;
		border-radius: 1.5rem;
	}

	/* Enhanced hover effects */
	.benefit-card:hover {
		transform: translateY(-5px);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.benefit-card:hover .icon-ring {
		transform: scale(1.1) rotate(45deg);
		opacity: 0.4;
	}

	.benefit-card:hover .icon-ring::after {
		transform: scale(1.2) rotate(-45deg);
		opacity: 0.2;
	}

	.benefit-card:hover .card-background {
		opacity: 1;
	}

	/* Add animation for icon */
	.benefit-icon-wrapper i {
		font-size: 1.8rem;
		color: var(--background-color);
		position: relative;
		z-index: 2;
		line-height: 60px;
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-icon-wrapper i {
		transform: scale(1.1);
	}

	/* Add a subtle transition for text */
	.benefit-content h3,
	.benefit-content p {
		transition: transform 0.3s ease;
	}

	.benefit-card:hover .benefit-content h3 {
		transform: translateY(-2px);
	}

	.benefit-card:hover .benefit-content p {
		transform: translateY(-1px);
	}

	/* Update the icon ring styles */
	.icon-ring {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100%;
		height: 100%;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.2;
		transition: all 0.3s ease;
	}

	.icon-ring::after {
		content: '';
		position: absolute;
		top: -8px;
		left: -8px;
		right: -8px;
		bottom: -8px;
		border: 2px solid var(--background-color);
		border-radius: 50%;
		opacity: 0.1;
		transition: all 0.3s ease;
	}

	/* Update hover animations to keep position fixed */
	.benefit-card:hover .icon-ring {
		opacity: 0.5;
		transform: translate(-50%, -50%) rotate(45deg);
	}

	.benefit-card:hover .icon-ring::after {
		opacity: 0.3;
		transform: rotate(-45deg);
	}

	/* Update Testimonials styles */
	.testimonials {
		padding: 6rem 5%;
		background-color: var(--services-background-color);
		position: relative;
		overflow: hidden;
	}

	.testimonials-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 2.5rem;
		max-width: 1200px;
		margin: 4rem auto 0;
		padding: 1rem;
		position: relative;
	}

	.testimonial-card {
		background-color: var(--text-color);
		padding: 3rem 2rem 2rem;
		border-radius: 1.5rem;
		position: relative;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
		transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1);
		animation: fadeInUp 0.8s ease forwards;
		animation-delay: var(--delay);
		opacity: 0;
		display: flex;
		flex-direction: column;
		height: 100%;
	}

	.testimonial-icon {
		position: absolute;
		top: -30px;
		left: 50%;
		transform: translateX(-50%);
		width: 60px;
		height: 60px;
		background: var(--services-background-color);
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
	}

	.testimonial-icon i {
		font-size: 1.8rem;
		color: var(--text-color);
		position: relative;
		z-index: 2;
		transition: transform 0.3s ease;
	}

	.rating {
		color: #ffd700;
		margin-bottom: 1.5rem;
		font-size: 1.1rem;
		text-align: center;
	}

	.testimonial-card p {
		color: var(--services-text-color);
		font-size: 1.1rem;
		line-height: 1.7;
		margin-bottom: 2rem;
		position: relative;
		z-index: 1;
		flex-grow: 1;
		text-align: center;
		font-style: italic;
	}

	.client-info {
		border-top: 1px solid rgba(52, 179, 138, 0.1);
		margin-top: auto;
		padding-top: 1.5rem;
		position: relative;
		z-index: 1;
	}

	.client-profile {
		display: flex;
		align-items: center;
		gap: 1rem;
		margin-bottom: 0.8rem;
	}

	.client-image {
		position: relative;
	}

	.client-info img {
		width: 55px;
		height: 55px;
		border-radius: 1rem;
		border: 3px solid var(--services-background-color);
		transition: all 0.4s ease;
	}

	.client-status {
		position: absolute;
		bottom: -4px;
		right: -4px;
		width: 18px;
		height: 18px;
		background: var(--background-color);
		border: 2px solid white;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.client-status i {
		color: white;
		font-size: 0.7rem;
	}

	.client-details {
		flex: 1;
	}

	.client-details strong {
		display: block;
		color: var(--services-text-color);
		font-size: 1.1rem;
		font-weight: 700;
		letter-spacing: 0.5px;
		margin-bottom: 0.2rem;
	}

	.client-details span {
		display: block;
		color: var(--services-text-color);
		opacity: 0.7;
		font-size: 0.9rem;
	}

	.client-meta {
		display: flex;
		align-items: center;
		justify-content: space-between;
		margin-top: 0.8rem;
	}

	.company {
		color: var(--background-color);
		font-size: 0.9rem;
		font-weight: 600;
		display: flex;
		align-items: center;
		gap: 0.5rem;
	}

	.company i {
		font-size: 1rem;
		opacity: 0.8;
	}

	.verified-badge {
		background: var(--services-background-color);
		color: var(--text-color);
		padding: 0.4rem 0.8rem;
		border-radius: 2rem;
		font-size: 0.8rem;
		display: flex;
		align-items: center;
		gap: 0.3rem;
		transition: all 0.3s ease;
	}

	.verified-badge i {
		font-size: 0.8rem;
	}

	/* Enhanced hover effects */
	.testimonial-card:hover img {
		transform: scale(1.05);
		border-color: var(--background-color);
	}

	.testimonial-card:hover .verified-badge {
		background: var(--background-color);
		transform: scale(1.05);
	}

	.testimonial-card:hover .client-status {
		transform: scale(1.1);
	}

	.client-info img {
		width: 55px;
		height: 55px;
		border-radius: 1rem;
		border: 3px solid var(--services-background-color);
		transition: all 0.4s ease;
	}

	.client-status {
		position: absolute;
		bottom: -4px;
		right: -4px;
		width: 18px;
		height: 18px;
		background: var(--background-color);
		border: 2px solid white;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.client-status i {
		color: white;
		font-size: 0.7rem;
	}

	.client-details {
		flex: 1;
	}

	.client-details strong {
		display: block;
		color: var(--services-text-color);
		font-size: 1.1rem;
		font-weight: 700;
		letter-spacing: 0.5px;
		margin-bottom: 0.2rem;
	}

	.client-details span {
		display: block;
		color: var(--services-text-color);
		opacity: 0.7;
		font-size: 0.9rem;
	}

	.client-meta {
		display: flex;
		align-items: center;
		justify-content: space-between;
		margin-top: 0.8rem;
	}

	.company {
		color: var(--background-color);
		font-size: 0.9rem;
		font-weight: 600;
		display: flex;
		align-items: center;
		gap: 0.5rem;
	}

	.company i {
		font-size: 1rem;
		opacity: 0.8;
	}

	.verified-badge {
		background: var(--services-background-color);
		color: var(--text-color);
		padding: 0.4rem 0.8rem;
		border-radius: 2rem;
		font-size: 0.8rem;
		display: flex;
		align-items: center;
		gap: 0.3rem;
		transition: all 0.3s ease;
	}

	.verified-badge i {
		font-size: 0.8rem;
	}

	/* Enhanced hover effects */
	.testimonial-card:hover img {
		transform: scale(1.05);
		border-color: var(--background-color);
	}

	.testimonial-card:hover .verified-badge {
		background: var(--background-color);
		transform: scale(1.05);
	}

	.testimonial-card:hover .client-status {
		transform: scale(1.1);
	}
</style>
