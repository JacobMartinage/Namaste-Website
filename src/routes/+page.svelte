<script>
    
    // This is a website for an indian/nepalese restaurant named "HammroKitchen". It has located near Virginia Tech, Blacksburg, VA. and should embody the school spirit of Virginia Tech.
    
    import { onMount } from 'svelte';

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
    background: url('/landing.png') no-repeat center center fixed; 
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    scroll-behavior: smooth;
    background-position: center;
    }
    nav {
    background-color: rgba(221, 161, 168, 0.8); /* Changed to translucent */
    color: #fff;
    padding: 0.5em; /* Reduced padding to make nav bar smaller */
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    width: 100%;
    font-size: 1em;
    font-family: 'Slabo 27px', serif;
  }
  nav ul {
    list-style-type: none;
    padding: 0;
    display: flex;
    justify-content: space-around;
  }
  nav ul li {
    margin-right: 0.5em; /* Reduced margin to match reduced nav bar size */
  }
  nav ul li a {
    color: #fff;
    text-decoration: none;
    font-family: 'Arial', sans-serif; /* Example font to fit theme */
  }
  nav ul li a:hover {
    color: #ff6347; /* Change the color to tomato when hovered over */
  }

  .active {
    font-weight: bold;
  }

  #about {
    display: flex;
    align-items: center;
    justify-content: space-around;
    padding: 2em;
    background-color: rgba(153, 51, 51, 0.8); /* Chicago maroon */
    color: #FFF; /* Burnt orange */
    flex-direction: column;
    /* background: url('/about.png') no-repeat center center; */
    background-size: cover;

  }
  #about h2 {
    font-family: 'Slabo 27px', serif;
    font-size: 4em;
    margin-bottom: 1em;
  }
  #about img {
    max-width: 200px;
    border-radius: 50%;
    border: 5px solid #FF6600; /* Burnt orange border */
  }
  #about p {
    font-size: 1.8em; /* Increase the font size */
    line-height: 1.6; /* Adjust the line height */
    margin-bottom: 1em; /* Add some margin */
    font-family: 'Slabo 27px', serif;
    text-align: center;
  }
  #landing {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; /* Full viewport height */
    background-position: center;
  }
  #company-logo {
    max-width: 25%; /* Make the logo a quarter of its current width */
    height: auto; /* Keep the aspect ratio */
  }
  #about h3 {
    font-family: 'Slabo 27px', serif;
  font-size: 2.2em;
  color: #ddd; /* Burnt orange */
  font-weight: bold;
}
#about .about-content {
    display: flex;
    flex-direction: column;
  }
  #about .about-content div {
    width: 60%;
    margin: 1em auto;
  }
  #about h2, #about h3 {
    text-align: center;
  }
  .about-section {
    transition: opacity 0.5s ease, transform 0.5s ease; /* Add a transition effect */
  }
.about-img {
    display: block;
    margin: 0 auto;
  }

  #menu {
    text-align: center;
    padding: 3em 0;
    background-color: rgba(153, 51, 51, 0.8); /* 80% opaque maroon */
    color: #fff; /* White text */
    font-size: 2.4em;
    font-family: 'Slabo 27px', serif;
  }
  .menu-button {
    display: inline-block;
    margin-top: 1em;
    padding: 0.5em 1em;
    background-color: #fff; /* White button */
    color: #993333; /* Maroon text */
    text-decoration: none;
    border-radius: 5px;
    transition: background-color 0.3s;
  }
  .menu-button:hover {
    background-color: #ccc; /* Light grey when hovered */
    color: #660000; /* Darker maroon when hovered */
  }
  #contact {
    text-align: center;
    padding: 2em 0;
    background-color: rgba(153, 51, 51, 0.8); /* 80% opaque maroon */
    color: #fff; /* White text */
    font-size: 2.4em;
    font-family: 'Slabo 27px', serif;
  }
  
  .social-button {
    display: inline-block;
    margin: 1em; /* Add margin around the buttons */
    width: 50px; /* Adjust as needed */
    height: 50px; /* Adjust as needed */
    transition: opacity 0.3s;
  }
  .social-button:hover {
    opacity: 0.7; /* Slightly transparent when hovered */
  }
  .social-button.email { /* Add a new class for the email button */
    width: 60px; /* Make the email logo a bit wider */
  }
  #contact p {
    font-size: 0.8em; /* Increase the font size */
    margin-bottom: 1em; /* Add some margin */
    font-family: 'Slabo 27px', serif;
    text-align: center;
  }

  #hours {
    text-align: center;
    padding: 2em 0;
    background-color: rgba(153, 51, 51, 0.8); /* 80% opaque maroon */
    color: #fff; /* White text */
    font-size: 2.4em;
    font-family: 'Slabo 27px', serif;
    align-items: center;
    display: flex;
    flex-direction: column;
  }

  #hours p {
    font-size: 0.8em; /* Increase the font size */
    margin-bottom: 1em; /* Add some margin */
    font-family: 'Slabo 27px', serif;
    text-align: center;
  }

  .hours-grid {
    align-self: center;
    width:50%;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.1em; /* Reduce the gap between the columns */
    text-align: left;
  }
  .sunday {
    text-align: center;
    margin-top: 1em;
  }
  nav ul li a {
    color: #fff;
    text-decoration: none;
    font-family: 'Arial', sans-serif; /* Example font to fit theme */
    font-size: 1.2em; /* Adjust the font size */
    padding: 0.5em; /* Add some padding */
  }

  @media only screen and (max-width: 767px) {
    nav ul {
      align-items: center;
      font-size: 0.2em;
    }

    nav ul li {
      margin: 0.5em 0;
    }

    .about-section {
      font-size: 0.5em;
    }

    #hours p{
        font-size: 0.5em;
    }
    #landing {
      background-position: center;
      background: url('/mobilebg.png'); 
    }
    body{
      background-size: cover;
      background: url('/mobilebg.png');
    }
}
  </style>
  <body>
  <nav>
    <ul>
        <li><a href="#landing" on:click={scrollToSection}>Home</a></li>
        <li><a href="#about" on:click={scrollToSection}>About</a></li>
        <li><a href="#menu" on:click={scrollToSection}>Menu</a></li>
        <li><a href="#hours" on:click={scrollToSection}>Hours</a></li>
        <li><a href="#contact" on:click={scrollToSection}>Contact</a></li>
    </ul>
  </nav>

  <section id="landing">
    <img src="logo.png" alt="Company Logo" id="company-logo" />
  </section>
  
  <section id="about">
    <h2>About Us</h2>
    <div class="about-content">
        <div class="about-section" id="owner-info">.
            <img class="about-img" src="owner.png" alt="Owner's Picture" />
        <h3>John Doe, Founder</h3>
        <p>
          Our story began in the heart of Nepal, where our founder, John Doe, was born and raised. Growing up in a culture rich with culinary traditions, John was introduced to the unique flavors and techniques of Nepali cuisine from a young age.
        </p>
      </div>
      <div class="about-section" id="nepali-food">
        <img class="about-img" src="owner.png" alt="Nepali Food" />
        <p>
          What makes Nepali food special is its fusion of flavors. Influenced by its neighboring countries, India, Tibet, and China, Nepali cuisine is a delightful blend of taste and texture. The use of local herbs and spices, combined with traditional cooking methods, results in dishes that are both flavorful and nutritious.
        </p>
      </div>
      <div class="about-section" id="our-mission">
        <img class="about-img" src="owner.png" alt="Our Mission" />
        <p>
          At our restaurant, we aim to bring the authentic taste of Nepal to your plate. We believe in preserving the traditional recipes while also adding our unique twist. We hope you enjoy the journey of flavors as much as we enjoy preparing them for you.
        </p>
      </div>
    </div>
  </section>
  
  <section id="menu">
    <h2>Our Menu</h2>
    <p>Discover the authentic taste of Nepal. Click the button below to explore our menu.</p>
    <a href="/menu" class="menu-button">View Menu</a>
  </section>
  <section id="hours">
    <h2>Our Hours</h2>
    <div class="hours-grid">
      <div>
        <p><strong>Monday:</strong> <br> 10:30am - 3pm<br> 5pm - 10pm</p>
        <p><strong>Wednesday:</strong> <br> 10:30am - 3pm<br> 5pm - 10pm</p>
        <p><strong>Friday:</strong> <br> 10:30am - 3pm<br> 5pm - 11pm</p>
      </div>
      <div>
        <p><strong>Tuesday:</strong> <br> Closed</p>
        <p><strong>Thursday:</strong> <br> 10:30am - 3pm<br> 5pm - 10pm</p>
        <p><strong>Saturday:</strong> <br> 10:30am - 3pm<br> 5pm - 11pm</p>
      </div>
    </div>
    <p class="sunday"><strong>Sunday:</strong> <br> 10:30am - 3pm<br> 5pm - 10pm</p>
  </section>

<section id="contact">
  <h2>Contact Us</h2>
  <p>We'd love to hear from you! You can reach us at:</p>
  <p><strong>Phone:</strong> (123) 456-7890</p>
  <p><strong>Email:</strong> info@restaurant.com</p>
  <p><strong>Address:</strong> 123 Main St, Anytown, USA</p>
  <a href="tel:1234567890">
    <img src="phone.png" alt="Call us" class="social-button" />
  </a>
  <a href="mailto:info@restaurant.com">
    <img src="email.png" alt="Email us" class="social-button email" />
  </a>
  <a href="https://www.facebook.com/restaurant" target="_blank">
    <img src="facebook.png" alt="Visit us on Facebook" class="social-button" />
  </a>
</section>
</body>