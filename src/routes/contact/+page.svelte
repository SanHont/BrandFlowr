<script>
	import Menu from '$lib/components/menu.svelte';
	import Footer from '$lib/components/footer.svelte';
	import ContactHero from '$lib/components/contact/ContactHero.svelte';
	import ContactForm from '$lib/components/contact/ContactForm.svelte';
	import QuickConnect from '$lib/components/contact/QuickConnect.svelte';
	import FAQ from '$lib/components/contact/FAQ.svelte';
</script>

<Menu />

<main>
	<div class="page-container">
		<ContactHero />
	</div>

	<div class="contact-grid">
		<div class="main-content">
			<ContactForm />
		</div>

		<div class="side-content">
			<QuickConnect />
		</div>

		<FAQ />
	</div>
</main>

<Footer />

<style>
	main {
		margin-top: 8rem;
		min-height: 100vh;
		background-color: var(--brand-primary);
	}

	.page-container {
		max-width: 90%;
		margin: 0 auto;
		padding: 0 5%;
	}

	.contact-grid {
		max-width: 90%;
		margin: 0 auto;
		padding: 2rem 5% 6rem;
		display: grid;
		grid-template-columns: 2fr 1fr;
		gap: 2rem;
		align-items: stretch;
	}

	.main-content,
	.side-content {
		display: flex;
		flex-direction: column;
		gap: 2rem;
		height: 100%;
	}

	@media (max-width: 968px) {
		.contact-grid {
			grid-template-columns: 1fr;
		}
	}
</style>
