<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Fusion Grove | Modern Culinary Artistry</title>
  <!-- Google Fonts + Smooth Font Rendering -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&family=Cormorant+Garamond:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet">
  <!-- Font Awesome 6 (Free Icons) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0A0C0F;
      font-family: 'Inter', sans-serif;
      color: #EDEDED;
      scroll-behavior: smooth;
      overflow-x: hidden;
    }

    /* Custom scrollbar */
    ::-webkit-scrollbar {
      width: 6px;
    }
    ::-webkit-scrollbar-track {
      background: #1a1e24;
    }
    ::-webkit-scrollbar-thumb {
      background: #C49A6C;
      border-radius: 8px;
    }

    /* animated gradient background for sections */
    .bg-glow {
      position: relative;
    }
    .bg-glow::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 20% 30%, rgba(196,154,108,0.08), transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    /* Navigation */
    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.5rem 5%;
      background: rgba(10, 12, 15, 0.85);
      backdrop-filter: blur(12px);
      position: fixed;
      width: 100%;
      top: 0;
      z-index: 1000;
      transition: all 0.3s ease;
      border-bottom: 1px solid rgba(196,154,108,0.2);
    }
    .logo {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.8rem;
      font-weight: 600;
      letter-spacing: 1px;
      background: linear-gradient(135deg, #E4C9A4, #C49A6C);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .nav-links {
      display: flex;
      gap: 2rem;
    }
    .nav-links a {
      text-decoration: none;
      color: #ddd;
      font-weight: 500;
      transition: 0.2s;
      position: relative;
    }
    .nav-links a:hover {
      color: #C49A6C;
    }
    .nav-links a::after {
      content: '';
      position: absolute;
      width: 0;
      height: 2px;
      bottom: -6px;
      left: 0;
      background: #C49A6C;
      transition: width 0.3s ease;
    }
    .nav-links a:hover::after {
      width: 100%;
    }

    /* Hero Section with AI inspired abstract overlay */
    .hero {
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      position: relative;
      overflow: hidden;
      background: #050608;
    }
    .hero-bg-layer {
      position: absolute;
      inset: 0;
      background-image: url('https://picsum.photos/id/104/1920/1080'); /* fallback artistic blur */
      background-size: cover;
      background-position: center;
      filter: brightness(0.35) blur(1px);
      transform: scale(1.02);
    }
    /* Abstract AI-style morphing gradient animations */
    .ai-overlay {
      position: absolute;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 30% 40%, rgba(210, 150, 80, 0.2), transparent 60%),
                  repeating-linear-gradient(45deg, rgba(255,215,150,0.02) 0px, rgba(255,215,150,0.02) 2px, transparent 2px, transparent 8px);
      pointer-events: none;
      animation: subtleShift 14s infinite alternate;
    }
    @keyframes subtleShift {
      0% { opacity: 0.4; transform: scale(1);}
      100% { opacity: 0.8; transform: scale(1.02);}
    }

    .hero-content {
      position: relative;
      z-index: 3;
      max-width: 900px;
      padding: 2rem;
      animation: fadeUp 1s ease-out;
    }
    .hero-content h1 {
      font-size: 4.5rem;
      font-family: 'Cormorant Garamond', serif;
      font-weight: 500;
      letter-spacing: -0.5px;
      background: linear-gradient(135deg, #F5E7D3, #D9B48B);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .hero-content p {
      font-size: 1.2rem;
      margin: 1.5rem 0;
      color: #ccc;
    }
    .btn-group {
      display: flex;
      gap: 1.5rem;
      justify-content: center;
    }
    .btn {
      padding: 0.9rem 2rem;
      border-radius: 40px;
      font-weight: 600;
      transition: all 0.4s cubic-bezier(0.2, 0.9, 0.4, 1.1);
      text-decoration: none;
      display: inline-block;
      backdrop-filter: blur(4px);
    }
    .btn-primary {
      background: #C49A6C;
      color: #0A0C0F;
      border: none;
      box-shadow: 0 6px 14px rgba(196,154,108,0.2);
    }
    .btn-primary:hover {
      background: #D9B48B;
      transform: translateY(-5px);
      box-shadow: 0 15px 30px rgba(196,154,108,0.4);
    }
    .btn-outline {
      border: 1px solid #C49A6C;
      color: #C49A6C;
      background: transparent;
    }
    .btn-outline:hover {
      background: rgba(196,154,108,0.15);
      transform: translateY(-3px);
      border-color: #E4C9A4;
    }

    /* Section styling */
    section {
      padding: 6rem 5%;
      position: relative;
    }
    .section-title {
      text-align: center;
      font-size: 2.8rem;
      font-family: 'Cormorant Garamond', serif;
      margin-bottom: 3rem;
      font-weight: 500;
      letter-spacing: -0.3px;
    }
    .section-title span {
      border-bottom: 3px solid #C49A6C;
      padding-bottom: 0.2rem;
    }

    /* Menu Grid - GOOGLE AI INSPIRED HOVER images (high quality unsplash-like) */
    .menu-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2.5rem;
      max-width: 1300px;
      margin: 0 auto;
    }
    .menu-card {
      background: #12161C;
      border-radius: 28px;
      overflow: hidden;
      transition: all 0.4s ease;
      cursor: pointer;
      box-shadow: 0 12px 20px -10px rgba(0,0,0,0.4);
      position: relative;
    }
    /* hover image effect (AI-style + zoom)  */
    .img-hover-ai {
      width: 100%;
      height: 240px;
      overflow: hidden;
      position: relative;
    }
    .img-hover-ai img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.5s cubic-bezier(0.2, 0.9, 0.4, 1.1), filter 0.4s;
      filter: brightness(0.92) contrast(1.02);
    }
    .menu-card:hover .img-hover-ai img {
      transform: scale(1.08);
      filter: brightness(1.02) contrast(1.05);
    }
    /* additional glow on hover - Google AI like micro-interaction */
    .menu-card:hover {
      transform: translateY(-10px);
      box-shadow: 0 28px 36px -12px rgba(196,154,108,0.3);
      border: 1px solid rgba(196,154,108,0.4);
    }
    .card-content {
      padding: 1.6rem;
    }
    .card-content h3 {
      font-size: 1.6rem;
      font-weight: 600;
      margin-bottom: 0.5rem;
    }
    .price {
      color: #C49A6C;
      font-weight: 700;
      font-size: 1.3rem;
      margin: 0.6rem 0;
    }
    .desc {
      color: #aaa;
      font-size: 0.9rem;
      line-height: 1.4;
    }

    /* Gallery section - AI style + hover parallax effect */
    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.8rem;
      max-width: 1300px;
      margin: 0 auto;
    }
    .gallery-item {
      border-radius: 24px;
      overflow: hidden;
      aspect-ratio: 1 / 1;
      position: relative;
      transition: all 0.3s;
    }
    .gallery-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.6s, filter 0.4s;
    }
    .gallery-item:hover img {
      transform: scale(1.05);
      filter: brightness(1.03) saturate(1.05);
    }
    .gallery-overlay {
      position: absolute;
      bottom: 0;
      background: linear-gradient(to top, #000000b3, transparent);
      width: 100%;
      padding: 1rem;
      opacity: 0;
      transition: 0.4s;
      color: white;
      font-weight: 500;
      text-align: center;
    }
    .gallery-item:hover .gallery-overlay {
      opacity: 1;
    }

    /* testimonials */
    .testimonial-wrapper {
      max-width: 900px;
      margin: 0 auto;
      text-align: center;
    }
    .testimonial-card {
      background: #12161C;
      padding: 2rem;
      border-radius: 2rem;
      margin: 1rem;
      transition: all 0.3s;
    }
    .testimonial-card i {
      font-size: 2rem;
      color: #C49A6C;
      margin-bottom: 1rem;
    }
    .testimonial-card p {
      font-size: 1.1rem;
      line-height: 1.5;
      font-style: italic;
    }
    .testimonial-card h4 {
      margin-top: 1rem;
      font-weight: 600;
    }

    /* reservation form */
    .reserve-form {
      max-width: 700px;
      margin: 0 auto;
      background: #101418cc;
      backdrop-filter: blur(12px);
      padding: 2.5rem;
      border-radius: 2rem;
      border: 1px solid rgba(196,154,108,0.3);
    }
    .form-group {
      margin-bottom: 1.5rem;
    }
    input, select, textarea {
      width: 100%;
      padding: 1rem;
      background: #1E242C;
      border: 1px solid #2C333C;
      border-radius: 1.5rem;
      color: #fff;
      font-size: 1rem;
      transition: 0.2s;
    }
    input:focus, select:focus, textarea:focus {
      outline: none;
      border-color: #C49A6C;
      box-shadow: 0 0 0 3px rgba(196,154,108,0.2);
    }
    .reserve-btn {
      background: #C49A6C;
      width: 100%;
      padding: 1rem;
      font-weight: bold;
      border: none;
      border-radius: 2rem;
      font-size: 1rem;
      cursor: pointer;
      transition: 0.3s;
      color: #0A0C0F;
    }
    .reserve-btn:hover {
      background: #D9B48B;
      letter-spacing: 1px;
      transform: scale(0.98);
    }

    /* footer */
    footer {
      background: #07090C;
      padding: 2rem 5%;
      text-align: center;
      border-top: 1px solid #1f242c;
    }
    .social-icons a {
      color: #C49A6C;
      margin: 0 0.8rem;
      font-size: 1.4rem;
      transition: 0.2s;
      display: inline-block;
    }
    .social-icons a:hover {
      transform: translateY(-4px);
      color: #F5E7D3;
    }

    /* typewriter animation for reservation alert */
    @keyframes fadeUp {
      0% { opacity: 0; transform: translateY(30px);}
      100% { opacity: 1; transform: translateY(0);}
    }

    /* mobile menu handling */
    @media (max-width: 800px) {
      .nav-links { gap: 1rem; }
      .hero-content h1 { font-size: 2.8rem; }
      .section-title { font-size: 2rem; }
      .btn-group { flex-direction: column; align-items: center; gap: 1rem;}
    }
  </style>
</head>
<body>

<nav class="navbar">
  <div class="logo">FUSION GROVE</div>
  <div class="nav-links">
    <a href="#home">Home</a>
    <a href="#menu">Menu</a>
    <a href="#gallery">Gallery</a>
    <a href="#reservations">Reserve</a>
  </div>
</nav>

<!-- Hero Section -->
<section id="home" class="hero" style="padding: 0;">
  <div class="hero-bg-layer"></div>
  <div class="ai-overlay"></div>
  <div class="hero-content">
    <h1>Where Art Meets <br> Culinary Intelligence</h1>
    <p>Experience an AI-inspired gastronomic journey — each plate is a masterpiece, each flavor tells a story.</p>
    <div class="btn-group">
      <a href="#menu" class="btn btn-primary">Explore Menu</a>
      <a href="#reservations" class="btn btn-outline">Book a Table</a>
    </div>
  </div>
</section>

<!-- MENU SECTION with GOOGLE AI IMAGES (curated high-res images via LoremFlick but using unsplash/loremflick? I use high-res picsum with style) -->
<section id="menu" class="bg-glow">
  <div class="section-title"><span>Signature Selections</span></div>
  <div class="menu-grid">
    <div class="menu-card">
      <div class="img-hover-ai"><img src="https://picsum.photos/id/127/500/350" alt="Grilled Octopus"></div>
      <div class="card-content">
        <h3>Ember Octopus</h3>
        <div class="price">$32</div>
        <div class="desc">Charred mediterranean octopus, smoked paprika, heirloom potatoes.</div>
      </div>
    </div>
    <div class="menu-card">
      <div class="img-hover-ai"><img src="https://picsum.photos/id/30/500/350" alt="Truffle Risotto"></div>
      <div class="card-content">
        <h3>AI Truffle Risotto</h3>
        <div class="price">$28</div>
        <div class="desc">Creamy arborio, black truffle, parmesan foam, and microgreens.</div>
      </div>
    </div>
    <div class="menu-card">
      <div class="img-hover-ai"><img src="https://picsum.photos/id/106/500/350" alt="Wagyu Steak"></div>
      <div class="card-content">
        <h3>Miso Wagyu</h3>
        <div class="price">$58</div>
        <div class="desc">Japanese A5 wagyu, miso glaze, crispy onion, nori dust.</div>
      </div>
    </div>
    <div class="menu-card">
      <div class="img-hover-ai"><img src="https://picsum.photos/id/119/500/350" alt="Lava Cake"></div>
      <div class="card-content">
        <h3>Chocolate Lava</h3>
        <div class="price">$14</div>
        <div class="desc">Molten dark chocolate core, vanilla bean gelato, gold leaf.</div>
      </div>
    </div>
  </div>
</section>

<!-- Gallery Section with AI style hover and images -->
<section id="gallery" style="background: #0C0F14;">
  <div class="section-title"><span>Visual Geometry</span></div>
  <div class="gallery-grid">
    <div class="gallery-item"><img src="https://picsum.photos/id/127/600/600" alt="dining experience"><div class="gallery-overlay">Ethereal Ambience</div></div>
    <div class="gallery-item"><img src="https://picsum.photos/id/20/600/600" alt="signature cocktail"><div class="gallery-overlay">Liquid Art</div></div>
    <div class="gallery-item"><img src="https://picsum.photos/id/40/600/600" alt="plating"><div class="gallery-overlay">AI Plating Tech</div></div>
    <div class="gallery-item"><img src="https://picsum.photos/id/29/600/600" alt="chef special"><div class="gallery-overlay">Chef’s Theater</div></div>
  </div>
</section>

<!-- Testimonials -->
<section>
  <div class="section-title"><span>Guest Stories</span></div>
  <div class="testimonial-wrapper">
    <div class="testimonial-card">
      <i class="fas fa-quote-left"></i>
      <p>"An astonishing fusion of AI creativity and culinary passion. Every dish looked like generative art — and tasted even better!"</p>
      <h4>— Maya Chen, Food & Tech Critic</h4>
    </div>
    <div class="testimonial-card">
      <i class="fas fa-star-of-life"></i>
      <p>"The hover effects on their website? Almost as mesmerizing as the wagyu. Highly recommended for special occasions."</p>
      <h4>— David K.</h4>
    </div>
  </div>
</section>

<!-- Reservation Form -->
<section id="reservations">
  <div class="section-title"><span>Secure Your Table</span></div>
  <div class="reserve-form">
    <form id="bookingForm">
      <div class="form-group"><input type="text" id="name" placeholder="Full Name" required></div>
      <div class="form-group"><input type="email" id="email" placeholder="Email Address" required></div>
      <div class="form-group"><input type="tel" id="phone" placeholder="Phone Number"></div>
      <div class="form-group"><input type="date" id="date" required></div>
      <div class="form-group"><select id="guests"><option>1 Guest</option><option>2 Guests</option><option>3 Guests</option><option>4+ Guests</option></select></div>
      <div class="form-group"><textarea rows="2" placeholder="Special requests / allergies..."></textarea></div>
      <button type="submit" class="reserve-btn">Reserve Experience <i class="fas fa-arrow-right"></i></button>
    </form>
  </div>
</section>

<!-- Footer -->
<footer>
  <div class="social-icons">
    <a href="#"><i class="fab fa-instagram"></i></a>
    <a href="#"><i class="fab fa-twitter"></i></a>
    <a href="#"><i class="fab fa-facebook-f"></i></a>
    <a href="#"><i class="fab fa-google"></i></a>
  </div>
  <p style="margin-top: 1.5rem;">&copy; 2025 Fusion Grove — AI-Inspired Hospitality | All images simulated for demo</p>
</footer>

<script>
  // Smooth scroll for anchor links + dynamic navbar background on scroll
  document.querySelectorAll('.nav-links a, .btn-primary, .btn-outline').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
      const targetId = this.getAttribute('href');
      if (targetId && targetId.startsWith('#')) {
        e.preventDefault();
        const targetElement = document.querySelector(targetId);
        if (targetElement) {
          targetElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
      }
    });
  });

  // Sticky navbar effect + transparency enhancement
  window.addEventListener('scroll', () => {
    const navbar = document.querySelector('.navbar');
    if (window.scrollY > 50) {
      navbar.style.background = 'rgba(10, 12, 15, 0.96)';
      navbar.style.backdropFilter = 'blur(16px)';
    } else {
      navbar.style.background = 'rgba(10, 12, 15, 0.85)';
    }
  });

  // Reservation form handling with beautiful toast animation
  const form = document.getElementById('bookingForm');
  if (form) {
    form.addEventListener('submit', (e) => {
      e.preventDefault();
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const date = document.getElementById('date').value;
      if (!name || !email || !date) {
        showFloatingMessage("Please fill in all required fields ✨", "#C49A6C");
        return;
      }
      // Simulate AI booking confirmation
      showFloatingMessage(`Thank you ${name}! Your AI-curated table is reserved. A confirmation will be sent to ${email}.`, "#C49A6C");
      form.reset();
    });
  }

  function showFloatingMessage(msg, borderColor) {
    // Create dynamic animated message notification
    let toast = document.createElement('div');
    toast.innerText = msg;
    toast.style.position = 'fixed';
    toast.style.bottom = '30px';
    toast.style.left = '50%';
    toast.style.transform = 'translateX(-50%)';
    toast.style.background = '#12161C';
    toast.style.color = '#F2E8CF';
    toast.style.padding = '1rem 2rem';
    toast.style.borderRadius = '50px';
    toast.style.borderLeft = `6px solid ${borderColor}`;
    toast.style.boxShadow = '0 15px 35px rgba(0,0,0,0.5)';
    toast.style.fontWeight = '500';
    toast.style.backdropFilter = 'blur(12px)';
    toast.style.zIndex = '2000';
    toast.style.fontFamily = "'Inter', sans-serif";
    toast.style.letterSpacing = '0.3px';
    toast.style.animation = 'fadeUp 0.3s ease';
    document.body.appendChild(toast);
    setTimeout(() => {
      toast.style.opacity = '0';
      toast.style.transition = 'opacity 0.5s';
      setTimeout(() => toast.remove(), 500);
    }, 3200);
  }
  
  // Additional micro-interaction: Scroll reveal for cards (simple intersection observer)
  const fadeElements = document.querySelectorAll('.menu-card, .gallery-item, .testimonial-card');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = '1';
        entry.target.style.transform = 'translateY(0px)';
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -10px 0px' });
  
  fadeElements.forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(25px)';
    el.style.transition = 'opacity 0.6s ease, transform 0.5s ease';
    observer.observe(el);
  });
  
  // Additional hover AI like glow effect for images on menu cards (already have)
  console.log("Google-AI inspired visual restaurant ready");
  
  // Optional: dummy dynamic year
  document.querySelector('footer p').innerHTML = `&copy; ${new Date().getFullYear()} Fusion Grove — AI-Inspired Hospitality | Art meets intelligence`;
</script>

</body>
</html>
