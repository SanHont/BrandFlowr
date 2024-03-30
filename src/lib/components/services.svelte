<section>
	<h2>Our Services</h2>
	<div class="services">
		<div class="card">
			<img src="assets/socialmedia.svg" alt="Our social media services" loading="lazy"/>
			<h3>Social Media</h3>
			<div class="line"></div>
			<p class="first-text">
				"Optimize brand visibility and engagement across platforms. Our social media experts handle
				content creation, management, and enhance your presence on Instagram, Facebook, and more."
			</p>
			<!-- <p class="second-text">
				Nowadays, social media platforms are the most useful ways to spread your brand. It is also
				the perfect way to create engagement with your potential customers. Our social media experts
				will make sure that your brand’s portrayal will reach its designated audience. BrandFlowr
				does everything from creating content to a full management of your social media accounts.
				With doing this we help you with creating a better presence on platforms like Instagram,
				Facebook and more.
			</p> -->
			<!-- <h4>Learn More</h4> -->
		</div>
		<div class="card">
			<img src="assets/programming.svg" alt="Our webdevelopment services" loading="lazy" />
			<h3>Web Development</h3>
			<div class="line"></div>
			<p class="first-text">
				"A must in the 21st century, your business website is the first impression and online
				business card. BrandFlowr ensures vitality and impact."
			</p>
			<!-- <p class="second-text">
				Having a website for your business is a mandatory thing in the 21st century. First thing
				potential customers do when they hear about a company is visit their website. This way your
				website is not only your first impression, but your online business card as well. BrandFlowr
				creates well-developed websites, which will bring your business’ online presence to life.
			</p> -->
			<!-- <h4>Learn More</h4> -->
		</div>
		<div class="card">
			<img src="assets/photography.svg" alt="Our photography services" loading="lazy" />
			<h3>Photography</h3>
			<div class="line"></div>
			<p class="first-text">
				"Brandflowr's dedicated photographers & videographers create compelling online content for
				your business, ensuring a positive image and engagement on social media."
			</p>
			<!-- <p class="second-text">
				Brandflowr works together with a dedicated team of photographers & videographers who can
				help with creating online content for your business. Depending on the date of most recent
				photos and preference for which Social Media platform we can create regular posts for your
				company which will be seen by all of your potential customers around your area. These
				photographers and videographers capture the essence of your business through their lens and
				will give a good image of your company for everyone to see.
			</p> -->
			<!-- <h4>Learn More</h4> -->
		</div>
	</div>
</section>

<style>
	section {
		background-color: var(--services-background-color);
		padding: 20px;
	}

	section,
	.services,
	.card {
		display: flex;
	}

	section,
	.card {
		flex-direction: column;
		align-items: center;
	}

	img {
		height: 50%;
		margin: 1rem;
	}

	.line {
		background-color: var(--line-color);
		height: 0.3rem;
		width: 40%;
		margin: 1rem 0;
		border-radius: 1rem;
	}

	.services {
		line-height: 1.5;
		width: 85%;
	}

	.card {
		width: 30%;
		background-color: var(--text-color);
		margin: 20px;
		padding: 1rem;
		border-radius: 1rem;
		transition: 0.3s;
	}

	h2 {
		margin-bottom: 2rem;
	}

	h2,
	h3
	/* h4  */ {
		text-align: center;
	}

	h2,
	h3,
	/* h4, */
	p {
		color: var(--services-text-color);
	}

	/* h4 {
		margin-top: 1rem;
		border-bottom: 2px solid var(--line-color);
		border-left: 2px solid var(--line-color-transparent);
		border-right: 2px solid var(--line-color-transparent);
		border-top: 2px solid var(--line-color-transparent);
		padding: 0.2rem;
		transition: 0.3s;
	}

	h4:hover {
		border-left: 2px solid var(--line-color);
		border-right: 2px solid var(--line-color);
		border-top: 2px solid var(--line-color);
		cursor: pointer;
	} */

	.card:hover {
		scale: 105%;
	}

	@media only screen and (max-width: 1410px) {
		h3 {
			font-size: 1.6rem;
		}
	}

	@media only screen and (max-width: 1270px) {
		h2 {
			font-size: 4.5rem;
		}
		h3 {
			font-size: 1.4rem;
		}

		img {
			height: 40%;
		}
	}

	@media only screen and (max-width: 1080px) {
		h2 {
			font-size: 4rem;
		}
		h3 {
			font-size: 1.2rem;
		}

		img {
			height: 35%;
		}

		p {
			font-size: 0.9rem;
		}
	}

	@media only screen and (max-width: 960px) {
		h2 {
			font-size: 3.5rem;
		}
		h3 {
			font-size: 1rem;
		}

		img {
			height: 30%;
		}

		p {
			font-size: 0.8rem;
		}
	}

	@media only screen and (max-width: 850px) {
		h2 {
			margin-bottom: -0.5rem;
		}
		.services {
			flex-direction: column;
			align-items: center;
		}

		.card {
			width: 70%;
		}

		h3 {
			font-size: 1rem;
		}

		img {
			width: 50%;
			height: 30%;
		}

		p {
			max-width: 80%;
			font-size: 0.8rem;
		}
	}

	@media only screen and (max-width: 750px) {
		h2 {
			margin-bottom: -0.5rem;
		}
		.card {
			width: 70%;
		}
	}

	@media only screen and (max-width: 600px) {
		h2 {
			margin-bottom: -0.5rem;
		}
		.card {
			width: 80%;
		}
	}

	@media only screen and (max-width: 425px) {
		h2 {
			font-size: 2.8rem;
		}
		.card {
			width: 90%;
		}
	}

	@media only screen and (max-width: 350px) {
		h2 {
			font-size: 2.4rem;
			margin-bottom: -0.5rem;
		}
		.card {
			width: 100%;
		}
	}
</style>
