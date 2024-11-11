<script>
	import { onMount } from 'svelte';

	let calendlyLoaded = false;

	onMount(() => {
		// Load Calendly widget script
		const script = document.createElement('script');
		script.src = 'https://assets.calendly.com/assets/external/widget.js';
		script.async = true;
		
		script.onload = () => {
			calendlyLoaded = true;
		};

		document.head.appendChild(script);

		// Cleanup on component destroy
		return () => {
			document.head.removeChild(script);
		};
	});

	function openCalendly() {
		if (window.Calendly) {
			window.Calendly.initPopupWidget({
				url: 'https://calendly.com/contact-brandflowr/30min',
				prefill: {},
				text: 'Schedule time with us',
				color: '#34b38a',
				textColor: '#ffffff',
				branding: true
			});
		} else {
			console.error('Calendly is not loaded');
		}
	}
</script>

<section class="contact-info-card">
	<h2>Quick Connect</h2>

	<!-- Contact Cards -->
	<div class="contact-cards">
		<a href="mailto:info@brandflowr.com" class="info-card">
			<div class="card-icon">
				<i class="fa-solid fa-envelope-open-text"></i>
			</div>
			<div class="card-content">
				<h3>Email Us</h3>
				<p>contact@brandflowr.nl</p>
				<span>Response within 24h</span>
			</div>
		</a>

		<a href="https://wa.me/31612345678" class="info-card">
			<div class="card-icon">
				<i class="fa-brands fa-whatsapp"></i>
			</div>
			<div class="card-content">
				<h3>WhatsApp</h3>
				<p>+31 6 39 82 51 68</p>
				<span>Available 9:00 - 17:00</span>
			</div>
		</a>

		<a href="tel:+31612345678" class="info-card">
			<div class="card-icon">
				<i class="fa-solid fa-phone-volume"></i>
			</div>
			<div class="card-content">
				<h3>Call Us</h3>
				<p>+31 6 39 82 51 68</p>
				<span>Mon - Fri, 9:00 - 17:00</span>
			</div>
		</a>
	</div>

	<!-- Schedule Meeting Button -->
	<button class="schedule-btn" on:click={openCalendly}>
		<i class="fa-regular fa-calendar"></i>
		Schedule a Meeting
	</button>

	<!-- Business Hours -->
	<div class="business-hours">
		<div class="section-header">
			<i class="fa-regular fa-clock"></i>
			<h3>Business Hours</h3>
		</div>
		<div class="hours-list">
			<div class="hours-item">
				<span>Monday - Friday</span>
				<span>9:00 - 17:00</span>
			</div>
			<div class="hours-item closed">
				<span>Saturday - Sunday</span>
				<span>Closed</span>
			</div>
		</div>
	</div>

	<!-- Location -->
	<div class="location-info">
		<div class="section-header">
			<i class="fa-solid fa-location-dot"></i>
			<h3>Our Location</h3>
		</div>
		<div class="location-card">
			<p>Amsterdam, Netherlands</p>
		</div>
	</div>
</section>

<style>
	.contact-info-card {
		background: var(--bg-primary);
		padding: 2rem;
		border-radius: 1.5rem;
		box-shadow: var(--shadow-sm);
		height: 100%;
		display: flex;
		flex-direction: column;
	}

	h2 {
		font-family: 'Montserrat', sans-serif;
		font-weight: 700;
		color: var(--text-primary);
		font-size: 1.8rem;
		margin-bottom: 1rem;
	}

	.contact-cards {
		display: flex;
		flex-direction: column;
		gap: 1rem;
		flex: 1;
	}

	.info-card {
		display: flex;
		align-items: center;
		gap: 1rem;
		padding: 1.2rem;
		background: white;
		border-radius: 1rem;
		text-decoration: none;
		transition: all 0.3s ease;
		border: 2px solid transparent;
	}

	.info-card:hover {
		transform: translateY(-2px);
		border-color: var(--brand-primary);
		box-shadow: var(--shadow-sm);
	}

	.card-icon {
		width: 48px;
		height: 48px;
		display: flex;
		align-items: center;
		justify-content: center;
		background: var(--brand-primary);
		border-radius: 12px;
		transition: transform 0.3s ease;
	}

	.info-card:hover .card-icon {
		transform: scale(1.1);
	}

	.card-icon i {
		color: white;
		font-size: 1.25rem;
	}

	.card-content {
		flex: 1;
	}

	.card-content h3 {
		font-family: 'Montserrat', sans-serif;
		font-weight: 600;
		color: var(--text-primary);
		font-size: 1.1rem;
		margin-bottom: 0.2rem;
	}

	.card-content p {
		font-family: 'Montserrat', sans-serif;
		color: var(--brand-primary);
		font-size: 0.95rem;
		font-weight: 500;
		margin-bottom: 0.2rem;
	}

	.card-content span {
		font-family: 'Montserrat', sans-serif;
		color: var(--text-muted);
		font-size: 0.85rem;
	}

	.section-header {
		display: flex;
		align-items: center;
		gap: 0.8rem;
		margin: 2rem 0 1rem;
	}

	.section-header i {
		color: var(--brand-primary);
		font-size: 1.2rem;
	}

	.section-header h3 {
		font-family: 'Montserrat', sans-serif;
		font-weight: 600;
		color: var(--text-primary);
		font-size: 1.2rem;
		margin: 0;
	}

	.hours-list {
		background: white;
		border-radius: 1rem;
		overflow: hidden;
	}

	.hours-item {
		display: flex;
		justify-content: space-between;
		padding: 1rem;
		font-family: 'Montserrat', sans-serif;
	}

	.hours-item:not(:last-child) {
		border-bottom: 1px solid rgba(52, 179, 138, 0.1);
	}

	.hours-item span:first-child {
		color: var(--text-primary);
		font-weight: 500;
	}

	.hours-item span:last-child {
		color: var(--brand-primary);
		font-weight: 600;
	}

	.hours-item.closed span:last-child {
		color: #ff4757;
	}

	.location-card {
		background: white;
		padding: 1rem;
		border-radius: 1rem;
		margin-top: 0.5rem;
	}

	.location-card p {
		font-family: 'Montserrat', sans-serif;
		color: var(--text-primary);
		display: flex;
		align-items: center;
		gap: 0.5rem;
	}

	.schedule-btn {
		font-family: 'Montserrat', sans-serif;
		font-weight: 600;
		background: var(--brand-primary);
		color: var(--text-light);
		padding: 1.2rem 2rem;
		border: none;
		border-radius: 0.8rem;
		font-size: 1rem;
		cursor: pointer;
		transition: all 0.3s ease;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.8rem;
		width: 100%;
		margin-bottom: 2rem;
	}

	.schedule-btn:hover {
		background: var(--brand-primary-dark);
		transform: translateY(-2px);
	}

	.schedule-btn i {
		font-size: 1.2rem;
	}
</style>
