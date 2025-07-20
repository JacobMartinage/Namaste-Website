<script>
	import { onMount } from 'svelte';
	import { faPhone, faEnvelope } from '@fortawesome/free-solid-svg-icons';
	import { faFacebook } from '@fortawesome/free-brands-svg-icons';
	import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
	import MenuModal from '$lib/MenuModal.svelte';

	let isMenuOpen = false;

	function toggleMenu() {
		isMenuOpen = !isMenuOpen;
	}

	onMount(() => {
		const sections = document.querySelectorAll('.about-section');

		const observer = new IntersectionObserver(entries => {
			entries.forEach(entry => {
				if (entry.isIntersecting) {
					entry.target.style.opacity = 1;
					entry.target.style.transform = 'translateY(0)';
				} else {
					entry.target.style.opacity = 0;
					entry.target.style.transform = 'translateY(20px)';
				}
			});
		}, { threshold: 0.1 });

		sections.forEach(section => {
			section.style.opacity = 0;
			section.style.transform = 'translateY(20px)';
			observer.observe(section);
		});
	});

	function scrollToSection(event) {
		event.preventDefault();
		const sectionId = event.target.getAttribute('href');
		document.querySelector(sectionId).scrollIntoView({ behavior: 'smooth' });
	}
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Slabo+27px&display=swap');

	:global(body) {
		margin: 0;
		height: 100vh;
		overflow: hidden;
	}

	.background {
		background: url('/namaste_landing.png') no-repeat center center fixed;
		background-size: cover;
		position: fixed;
		width: 100%;
		height: 100%;
		z-index: -1;
	}

	.content {
		overflow-y: auto;
		height: 100vh;
	}

	nav {
		background-color: rgba(222, 120, 65, 1);
		color: #fff;
		padding: 0.5em;
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		width: 100%;
		font-size: 1em;
		font-family: 'Slabo 27px', serif;
		z-index: 1000;
	}

	nav ul {
		list-style-type: none;
		padding: 0;
		display: flex;
		justify-content: space-evenly;
	}

	nav ul li a {
		color: #fff;
		text-decoration: none;
		font-size: 1.2em;
		padding: 0.1em;
	}

	nav ul li a:hover {
		color: #000000;
		font-weight: bold;
	}

	#about, #menu, #hours, #contact, #order {
		text-align: center;
		padding: 1em 0;
		background-color: rgba(153, 51, 51, 0.8);
		color: #fff;
		font-size: 1.5em;
		font-family: 'Slabo 27px', serif;
		margin: 1em; /* Added margin for all sections */
	}

	.about-section {
		transition: opacity 0.5s ease, transform 0.5s ease;
	}

	.about-section p {
		margin: 1.5em 2em;
	}

	.about-img {
		display: block;
		margin: 0 auto;
		width: 40%; /* Increased size of the about image */
		height: auto;
		object-fit: cover;
		border-radius: 10px; /* Added rounding to the image */
	}

	.line-break {
		border-radius: 5px;
		height: 3px;
		background: #ffffff;
		width: 70%;
	}

	#landing {
		display: flex;
		justify-content: center;
		align-items: center;
		min-height: 100vh;
		margin-top: 14em;
		padding: 1em;
	}

	#company-logo {
		max-width: 25%;
		height: auto;
		width: auto;
	}

	#hours h2 {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 0.5em;
	}

	.hours-container {
		display: flex;
		justify-content: center;
		flex-wrap: wrap;
		max-width: 600px;
		margin: auto;
	}

	.hours-box {
		flex: 1;
		padding: 1em;
		min-width: 250px;
		text-align: left;
	}

	.hours-box p {
		font-size: 1.2em;
		margin: 0.5em 0;
		padding: 0.5em;
		border-radius: 5px;
		background: rgba(255, 255, 255, 0.1);
	}

	.closed {
		color: #ff6347;
		font-weight: bold;
	}

	#contact p {
		margin-left: 2em;
		margin-right: 2em;
	}

	@media only screen and (max-width: 767px) {
		.about-section {
			font-size: 0.8em;
		}

		.hours-box p {
			font-size: 1em;
		}

		#contact p {
			font-size: 0.8em;
		}
	}

	@media only screen and (max-width: 768px) {
		#company-logo {
			max-width: 80%;
			margin-top: -8em;
		}

		#landing {
			margin-top: 8em;
		}
		
		nav ul li.desktop-only {
			display: none;
		}
		
		nav ul {
			justify-content: space-between;
		}
	}

	.menu-button {
		display: inline-block;
		padding: 0.5em 1em;
		margin: 0.5em;
		background-color: rgba(222, 120, 65, 0.9);
		color: white;
		text-decoration: none;
		border-radius: 4px;
		cursor: pointer;
		&.order-now {
			background-color: rgba(34, 193, 195, 0.9);
		}
	}

	.menu-button:hover {
		background-color: rgb(0, 0, 0);
	}
</style>

<body>
	<div class="background"></div>
	<div class="content">
		<nav>
			<ul style="display: flex; align-items: center; justify-content: space-evenly;">
				<li><button class="menu-button" on:click={toggleMenu}>Menu</button></li>
				<li><a href="#landing" on:click={scrollToSection}>Home</a></li>
				<li class="desktop-only"><a href="#about" on:click={scrollToSection}>About</a></li>
				<li class="desktop-only"><a href="#hours" on:click={scrollToSection}>Hours</a></li>
				<li class="desktop-only"><a href="#contact" on:click={scrollToSection}>Contact</a></li>
				<li><a href="https://order.spoton.com/so-namaste-kitchen-22634/blacksburg-va/67afd30cb4ce2358bdb2121c" target="_blank" rel="noopener noreferrer"><button class="menu-button order-now">Order Now</button></a></li>
			</ul>
		</nav>

		<section id="landing">
			<img src="namaste_logo.png" alt="Company Logo" id="company-logo" />
		</section>

		<section id="about">
			<h2>About Us</h2>
			<div class="about-content">
				<div class="about-section">
					<img class="about-img" src="food3.png" alt="Owner's Picture" />
					<p>Experience the rich and authentic flavors of Nepal at Namaste Kitchen. We serve traditional Nepali dishes, crafted with fresh ingredients and spices that capture the essence of the Himalayas.</p>
				</div>
			</div>
		</section>

		<section id="menu">
			<hr class="line-break"/>
			<h2>Our Menu</h2>
			<p>Discover the authentic taste of Nepal.</p>
			<button class="menu-button" on:click={toggleMenu}>View Menu</button>
		</section>

		<section id="order">
			<hr class="line-break"/>
			<h2>Ready to Order?</h2>
			<p>Place your order online for pickup or delivery!</p>
			<a href="https://order.spoton.com/so-namaste-kitchen-22634/blacksburg-va/67afd30cb4ce2358bdb2121c" target="_blank" rel="noopener noreferrer">
				<button class="menu-button order-now">Order Now</button>
			</a>
		</section>

		<section id="hours">
			<hr class="line-break"/>
			<h2>⏰ Our Hours</h2>
			<div class="hours-container">
				<div class="hours-box">
					<p><strong>Monday</strong> <span class="closed">Closed</span></p>
					<p><strong>Tuesday</strong> <br> 11:00 AM - 3:00 PM <br> 5:00 PM - 10:00 PM</p>
					<p><strong>Wednesday</strong> <br> 11:00 AM - 3:00 PM <br> 5:00 PM - 10:00 PM</p>
					<p><strong>Thursday</strong> <br> 11:00 AM - 3:00 PM <br> 5:00 PM - 10:00 PM</p>
					<p><strong>Friday</strong> <br> 11:00 AM - 3:00 PM <br> 5:00 PM - 10:00 PM</p>
					<p><strong>Saturday</strong> <br> 11:00 AM - 3:00 PM <br> 5:00 PM - 10:00 PM</p>
					<p><strong>Sunday</strong> <br> 11:00 AM - 3:00 PM <br> 5:00 PM - 10:00 PM</p>
				</div>
			</div>
		</section>

		<section id="contact">
			<hr class="line-break"/>
			<h2>Contact Us</h2>
			<p>We'd love to hear from you! You can reach us at:</p>
			<p><strong>Phone:</strong> (540) 806-1219</p>
			<p><strong>Email:</strong> namastekitchen03@gmail.com</p>
			<p><strong>Address:</strong>  239 North Main Street, Blacksburg, VA</p>
			<!-- <a href="tel:5408061219" aria-label="Call us">
				<FontAwesomeIcon icon={faPhone} class="icon" />
			</a>
			<a href="mailto:namastekitchen03@gmail.com" aria-label="Email us">
				<FontAwesomeIcon icon={faEnvelope} class="icon" />
			</a>
			<a href="https://www.facebook.com/profile.php?id=100088281829800&mibextid=LQQJ4d" target="_blank" aria-label="Visit us on Facebook">
				<FontAwesomeIcon icon={faFacebook} class="icon" />
			</a> -->
		</section>

		<MenuModal isOpen={isMenuOpen} onClose={() => isMenuOpen = false} />
	</div>
</body>