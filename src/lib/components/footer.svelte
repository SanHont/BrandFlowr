<section>
	<div class="footer-container">
		<div class="footer-info">
			<h2>Contact Us</h2>
			<p>Email: <a href="mailto:contact@brandflowr.nl">contact@brandflowr.nl</a></p>
			<p>Phone: <a href="tel:+31641220044">+31 6 41 22 00 44</a></p>
			<p>KVK: 94536457</p>
			<p>BTW: NL866813032B01</p>
		</div>

		<div class="footer-social">
			<h2>Follow Us</h2>
			<ul class="social-icons">
				<li>
					<a href="https://www.facebook.com/profile.php?id=61557368016442"
						><img
							src="https://cdn-icons-png.flaticon.com/512/733/733547.png"
							alt="Click to go to our Facebook page"
						/></a
					>
				</li>
				<li>
					<a href="https://www.instagram.com/brandflowr/"
						><img
							src="https://cdn-icons-png.flaticon.com/512/2111/2111463.png"
							alt="Click to go to our Instagram page"
						/></a
					>
				</li>
				<li>
					<a href="https://www.linkedin.com/company/brandflowr/"
						><img
							src="https://cdn-icons-png.flaticon.com/512/145/145807.png"
							alt="Click to go to our LinkedIn page"
						/></a
					>
				</li>
			</ul>
		</div>
	</div>

	<div class="footer-bottom">
		<p>&copy; 2024 BrandFlowr. All rights reserved.</p>
	</div>
</section>

<style>
	section {
		background-color: var(--services-background-color);
		color: var(--text-color);
		padding: 50px 20px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.footer-container {
		display: flex;
		justify-content: center; /* Center the items horizontally */
		gap: 40px; /* Increase gap for more space between items */
		flex-wrap: wrap;
	}

	.footer-info,
	.footer-social {
		flex: 1 1 300px;
		text-align: center; /* Center text within each section */
	}

	.footer-info h2,
	.footer-social h2 {
		margin-bottom: 10px;
		font-size: 1.5rem;
		color: var(--services-text-color);
	}

	.footer-info p,
	.footer-social ul {
		margin: 0 0 10px;
		font-size: 1rem;
	}

	.footer-info a,
	.footer-social a {
		color: var(--text-color);
		text-decoration: none;
	}

	.footer-social ul {
		list-style: none;
		padding: 0;
		display: flex;
		justify-content: center; /* Center icons in social section */
		gap: 15px;
	}

	.footer-social ul li {
		display: inline-block;
	}

	.footer-social img {
		width: 4em;
		margin-top: 1em;
		filter: grayscale(100%);
		transition:
			filter 0.1s ease-in-out,
			transform 0.1s ease;
	}

	.footer-social img:hover {
		filter: none;
		transform: scale(1.1);
	}

	.footer-bottom {
		text-align: center;
		margin-top: 30px;
		border-top: 1px solid var(--line-color);
		padding-top: 15px;
	}

	.footer-bottom p {
		margin: 0;
		font-size: 0.9rem;
	}

	@media (max-width: 768px) {
		.footer-container {
			flex-direction: column;
			align-items: center;
		}
	}

	@media (max-width: 480px) {
		section {
			padding: 30px 10px;
		}

		.footer-info h2,
		.footer-social h2 {
			font-size: 1.3rem;
		}

		.footer-info p,
		.footer-social ul {
			font-size: 0.9rem;
		}
	}
</style>
