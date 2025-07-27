<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Oasis AI - Smart WhatsApp Auto-Reply</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #e0f7fa, #e0f2f1);
      color: #333;
      margin: 0;
      padding: 0;
      overflow-x: hidden;
    }
    header {
      background: #1b1f3b;
      color: #fff;
      padding: 3rem 1rem;
      text-align: center;
      position: relative;
      perspective: 1000px;
    }
    #logo {
      width: 120px;
      height: auto;
      margin-bottom: 1rem;
      transform-style: preserve-3d;
      transition: transform 0.3s ease;
    }
    header h1 {
      margin: 0;
      font-size: 3rem;
      z-index: 2;
      position: relative;
      transform-style: preserve-3d;
    }
    header p {
      font-size: 1.3rem;
      z-index: 2;
      position: relative;
      transform-style: preserve-3d;
    }
    .cta-button {
      display: inline-block;
      background: #0f9d58;
      color: white;
      padding: 1rem 2rem;
      border-radius: 50px;
      text-decoration: none;
      font-weight: bold;
      margin-top: 2rem;
      transition: background 0.3s ease, transform 0.3s ease;
      transform-style: preserve-3d;
    }
    .cta-button:hover {
      background: #0c7a43;
      transform: translateZ(20px);
    }
    .section {
      padding: 3rem 1rem;
      max-width: 1000px;
      margin: auto;
      text-align: center;
    }
    .features {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      margin-top: 2rem;
      perspective: 800px;
    }
    .feature {
      background: white;
      padding: 2rem;
      border-radius: 15px;
      box-shadow: 0 6px 20px rgba(0,0,0,0.1);
      transition: transform 0.3s ease;
      transform-style: preserve-3d;
    }
    .feature:hover {
      transform: rotateY(15deg) rotateX(10deg) translateZ(20px);
    }
    .feature h3 {
      color: #0f9d58;
    }
    footer {
      text-align: center;
      padding: 2rem;
      background: #1b1f3b;
      color: white;
    }
    canvas#stars {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      pointer-events: none;
    }
  </style>
</head>
<body>
  <canvas id="stars"></canvas>
  <header id="hero">
    <img id="logo" src="logo.png" alt="Oasis AI Logo">
    <h1>Oasis AI</h1>
    <p>Your Smart WhatsApp Auto-Reply Assistant</p>
    <a class="cta-button" href="https://wa.me/916291378773?text=Hi%2C%20I%20want%20Oasis%20AI%20setup">Try It Free Now</a>
  </header>  <section class="section">
    <h2>Why Choose Oasis AI?</h2>
    <div class="features">
      <div class="feature">
        <h3>✅ Instant Auto-Reply</h3>
        <p>Reply to customers 24/7 on WhatsApp, even while you sleep.</p>
      </div>
      <div class="feature">
        <h3>📦 Smart Buttons</h3>
        <p>Give customers choices like "Order Now", "View Menu", or "Track Order" instantly.</p>
      </div>
      <div class="feature">
        <h3>🚀 Free Setup</h3>
        <p>We set it up for you – no coding, no headache, completely free.</p>
      </div>
      <div class="feature">
        <h3>💼 Perfect for Small Businesses</h3>
        <p>Tailored for shops, coaches, agencies, online sellers, and service providers.</p>
      </div>
    </div>
  </section>  <section class="section">
    <h2>See Oasis AI in Action</h2>
    <p>Message us and watch Oasis reply to you within seconds.</p>
    <a class="cta-button" href="https://wa.me/916291378773?text=Hi%2C%20I%20want%20Oasis%20AI%20setup">💬 Try the Demo Now</a>
  </section>  <section class="section">
    <h2>Start Free – No Payment Needed</h2>
    <p>Get your WhatsApp AI assistant up and running in 10 minutes.</p>
    <a class="cta-button" href="https://wa.me/916291378773?text=Hi%2C%20I%20want%20Oasis%20AI%20setup">📲 Chat to Get Started</a>
  </section>  <footer>
    <p>&copy; 2025 Oasis AI. All rights reserved.</p>
  </footer>  <script>
    const canvas = document.getElementById('stars');
    const ctx = canvas.getContext('2d');
    let stars = [];

    function initStars() {
      stars = [];
      for (let i = 0; i < 100; i++) {
        stars.push({ x: Math.random() * canvas.width, y: Math.random() * canvas.height, radius: Math.random() * 1.5, alpha: Math.random(), speed: 0.005 + Math.random() * 0.01 });
      }
    }

    function drawStars() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      stars.forEach(star => {
        star.alpha += star.speed;
        if (star.alpha > 1 || star.alpha < 0) star.speed = -star.speed;
        ctx.beginPath();
        ctx.arc(star.x, star.y, star.radius, 0, 2 * Math.PI);
        ctx.fillStyle = `rgba(255, 255, 255, ${star.alpha})`;
        ctx.fill();
      });
      requestAnimationFrame(drawStars);
    }

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      initStars();
    }

    document.getElementById('hero').addEventListener('mousemove', e => {
      const { width, height, left, top } = e.currentTarget.getBoundingClientRect();
      const x = (e.clientX - left - width/2) / width * 30;
      const y = (e.clientY - top - height/2) / height * 30;
      document.getElementById('logo').style.transform = `rotateY(${x}deg) rotateX(${-y}deg)`;
      document.querySelector('header h1').style.transform = `rotateY(${x}deg) rotateX(${-y}deg)`;
    });

    document.getElementById('hero').addEventListener('mouseleave', () => {
      document.getElementById('logo').style.transform = '';
      document.querySelector('header h1').style.transform = '';
    });

    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();
    drawStars();
  </script></body>
</html>
