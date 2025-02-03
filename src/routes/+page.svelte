<script>
	import { onMount } from 'svelte';
	import { faPhone, faEnvelope } from '@fortawesome/free-solid-svg-icons';
	import { faFacebook } from '@fortawesome/free-brands-svg-icons';
	import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';

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
		background: url('/namaste_landing.png') no-repeat center center fixed;
		background-size: cover;
		scroll-behavior: smooth;
		background-position: center;
	}

	nav {
		background-color: rgba(222, 120, 65, 0.9);
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
		justify-content: space-around;
	}

	nav ul li a {
		color: #fff;
		text-decoration: none;
		font-size: 1.2em;
		padding: 0.5em;
	}

	nav ul li a:hover {
		color: #ff6347;
	}

	#about, #menu, #hours, #contact {
		text-align: center;
		padding: 2em 0;
		background-color: rgba(153, 51, 51, 0.8);
		color: #fff;
		font-size: 2em;
		font-family: 'Slabo 27px', serif;
	}

	.about-section {
		transition: opacity 0.5s ease, transform 0.5s ease;
	}

	.about-img {
		display: block;
		margin: 0 auto;
		width: 25%;
		aspect-ratio: 1;
	}

	#landing {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 100vh;
		background-position: center;
		margin-top: 14em;
	}

	#company-logo {
		max-width: 25%;
		height: auto;
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

	@media only screen and (max-width: 767px) {
		.about-section {
			font-size: 0.8em;
		}

		.hours-box p {
			font-size: 1em;
		}
	}
</style>

<body>
	<nav>
		<ul>
			<li><a href="#landing" on:click={scrollToSection}>Home</a></li>
			<li><a href="#about" on:click={scrollToSection}>About</a></li>
			<li><a href="/menu">Menu</a></li>
			<li><a href="#hours" on:click={scrollToSection}>Hours</a></li>
			<li><a href="#contact" on:click={scrollToSection}>Contact</a></li>
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
				<p>Experience the rich and authentic flavors of Nepal at Namaste Kitchen...</p>
			</div>
		</div>
	</section>

	<section id="menu">
		<h2>Our Menu</h2>
		<p>Discover the authentic taste of Nepal.</p>
		<a href="/menu" class="menu-button">View Menu</a>
		<a href="/order" class="menu-button">Order</a>
	</section>

	<section id="hours">
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
		<h2>Contact Us</h2>
		<p><strong>Phone:</strong> (540) 818-5767</p>
		<p><strong>Email:</strong> namastekitchen03@gmail.com</p>
		<p><strong>Address:</strong> 239 North Main Street, Blacksburg, VA</p>
	</section>
</body>
