<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const cursor = ref(null);

// Mouse follower
const onMouseMove = (e) => {
  if (!cursor.value) return;
  const x = e.clientX;
  const y = e.clientY;
  cursor.value.animate(
    {
      left: `${x}px`,
      top: `${y}px`,
    },
    { duration: 300, fill: "forwards" },
  );
};

onMounted(() => {
  window.addEventListener("mousemove", onMouseMove);

  // Intersection Observer for scroll animations
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("visible");
        }
      });
    },
    { threshold: 0.1 },
  );

  document.querySelectorAll(".reveal").forEach((el) => observer.observe(el));
});

onUnmounted(() => {
  window.removeEventListener("mousemove", onMouseMove);
});

const features = [
  {
    id: 1,
    title: "Ultra Fast",
    description:
      "Experience blazing fast performance with our optimized core algorithms.",
    icon: '<svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>',
  },
  {
    id: 2,
    title: "Secure Design",
    description: "Built with enterprise-ready security at its foundation.",
    icon: '<svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z" /></svg>',
  },
  {
    id: 3,
    title: "Scalable",
    description:
      "Ready to grow with your business to any size without compromises.",
    icon: '<svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M3 17l6-6 4 4 8-8M17 7h4v4" /></svg>',
  },
  {
    id: 4,
    title: "Interactive",
    description: "Engage your users with beautiful interactive elements.",
    icon: '<svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" /></svg>',
  },
  {
    id: 5,
    title: "Modern UI",
    description: "Sleek, futuristic, and premium glassmorphism design.",
    icon: '<svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4" /></svg>',
  },
  {
    id: 6,
    title: "No Backend",
    description: "Runs completely in the browser for maximum simplicity.",
    icon: '<svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><path stroke-linecap="round" stroke-linejoin="round" d="M2 12h20M12 2a15.3 15.3 0 014 10 15.3 15.3 0 01-4 10 15.3 15.3 0 01-4-10 15.3 15.3 0 014-10z"/></svg>',
  },
];

const pricingPlans = [
  {
    id: 1,
    name: "Starter",
    price: "Free",
    featureList: [
      "Basic UI components",
      "Community support",
      "Standard updates",
    ],
    link: "https://github.com/vuejs/core",
  },
  {
    id: 2,
    name: "Pro",
    price: "$49/mo",
    featureList: [
      "Premium animations",
      "Priority support",
      "Weekly updates",
      "Custom domain",
    ],
    link: "#",
  },
  {
    id: 3,
    name: "Enterprise",
    price: "Custom",
    featureList: [
      "Dedicated manager",
      "24/7 Phone support",
      "Custom integrations",
      "SLA guarantee",
    ],
    link: "mailto:contact@astra.design",
  },
];

const cards = ref(features);
const plans = ref(pricingPlans);
</script>

<template>
  <div class="app-container">
    <div id="blob" ref="cursor"></div>
    <div id="blob-blur"></div>

    <nav class="navbar reveal fade-down">
      <div class="logo">ASTRA<span>.</span></div>
      <div class="nav-links">
        <a href="#about">About</a>
        <a href="#features">Features</a>
        <a href="#pricing">Pricing</a>
        <a href="#pricing" class="btn-primary btn-link">Get Started</a>
      </div>
    </nav>

    <header class="hero">
      <div class="hero-content reveal fade-up">
        <h1 class="gradient-text">Shape the Future</h1>
        <p class="subtitle">
          Experience high-end design, flawless performance, and modern
          architecture. A premium digital experience specifically built to amaze
          your visitors.
        </p>
        <div class="cta-group">
          <a href="#pricing" class="btn-primary large btn-link"
            >Start Building</a
          >
          <a href="#features" class="btn-secondary large btn-link"
            >Explore Features</a
          >
        </div>
      </div>
      <div class="hero-graphic reveal scale-up" style="transition-delay: 200ms">
        <div class="floating-shape shape-1"></div>
        <div class="floating-shape shape-2"></div>
        <div class="floating-shape shape-3"></div>
      </div>
    </header>

    <section id="about" class="about-section reveal fade-up">
      <div class="about-container">
        <div class="about-text">
          <h2 class="section-title text-left">Who we are</h2>
          <p class="paragraph">
            We are a squad of digital creators pushing the bounds of web
            experiences. Our mission is to transform simple ideas into visually
            breathtaking, interactive masterpieces. Wait no more to reinvent
            your digital identity.
          </p>
          <div class="about-action">
            <a
              href="https://vuejs.org/guide/introduction.html"
              target="_blank"
              class="btn-secondary btn-link inline-btn"
              >Read our documentation &rarr;</a
            >
          </div>
        </div>
        <div class="about-stats glass">
          <div class="stat-item">
            <h3>10M+</h3>
            <p>Downloads</p>
          </div>
          <div class="stat-item">
            <h3>99.9%</h3>
            <p>Uptime</p>
          </div>
          <div class="stat-item">
            <h3>24/7</h3>
            <p>Support</p>
          </div>
        </div>
      </div>
    </section>

    <section id="features" class="features">
      <h2 class="section-title reveal fade-up">Why choose Astra?</h2>
      <div class="features-grid">
        <div
          v-for="(feature, index) in cards"
          :key="feature.id"
          class="feature-card glass reveal fade-up"
          :style="{ transitionDelay: `${(index % 3) * 150}ms` }"
        >
          <div class="icon-wrapper" v-html="feature.icon"></div>
          <h3>{{ feature.title }}</h3>
          <p>{{ feature.description }}</p>
        </div>
      </div>
    </section>

    <section id="pricing" class="pricing">
      <h2 class="section-title reveal fade-up">Simple Pricing</h2>
      <div class="pricing-grid">
        <div
          v-for="(plan, index) in plans"
          :key="plan.id"
          class="pricing-card glass reveal fade-up"
          :class="{ 'featured-plan': index === 1 }"
          :style="{ transitionDelay: `${index * 150}ms` }"
        >
          <div v-if="index === 1" class="popular-badge">Most Popular</div>
          <h3>{{ plan.name }}</h3>
          <div class="price">{{ plan.price }}</div>
          <ul class="features-list">
            <li v-for="feat in plan.featureList" :key="feat">
              <span class="check">✓</span> {{ feat }}
            </li>
          </ul>
          <a
            :href="plan.link"
            class="btn-primary btn-link full-width"
            :class="{ 'btn-secondary': index !== 1 }"
            >Choose Plan</a
          >
        </div>
      </div>
    </section>

    <footer class="footer reveal fade-up">
      <div class="footer-content">
        <div class="logo">ASTRA<span>.</span></div>
        <div class="social-links">
          <a href="#" class="social-link">Twitter</a>
          <a href="https://github.com" target="_blank" class="social-link"
            >GitHub</a
          >
          <a href="#" class="social-link">Discord</a>
        </div>
      </div>
      <p class="copyright">© 2026 Astra Design. All rights reserved.</p>
    </footer>
  </div>
</template>

<style scoped>
/* App container */
.app-container {
  min-height: 100vh;
  position: relative;
  overflow: hidden;
}

/* Base styles for anchors behaving as buttons */
.btn-link {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  text-align: center;
}

.full-width {
  width: 100%;
}

.inline-btn {
  padding: 0.8rem 1.5rem;
  font-size: 0.95rem;
}

/* Background blob effect */
#blob {
  position: fixed;
  background-color: white;
  height: 400px;
  width: 400px;
  border-radius: 50%;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background: linear-gradient(to right, var(--primary), var(--secondary));
  animation: rotate 20s infinite;
  z-index: -1;
  opacity: 0.6;
  pointer-events: none;
}

#blob-blur {
  position: fixed;
  height: 100vh;
  width: 100vw;
  z-index: -1;
  backdrop-filter: blur(120px);
  -webkit-backdrop-filter: blur(120px);
  pointer-events: none;
}

@keyframes rotate {
  from {
    transform: translate(-50%, -50%) rotate(0deg);
  }
  50% {
    transform: translate(-50%, -50%) scale(1, 1.5);
  }
  to {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}

/* Navbar */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 2rem 5%;
  position: relative;
  z-index: 10;
}

.logo {
  font-family: "Outfit", sans-serif;
  font-weight: 900;
  font-size: 1.8rem;
  letter-spacing: -1px;
}
.logo span {
  color: var(--primary);
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-links a:not(.btn-link) {
  color: var(--text-secondary);
  text-decoration: none;
  font-weight: 600;
  transition: color 0.3s ease;
}

.nav-links a:not(.btn-link):hover {
  color: var(--text-primary);
}

/* Buttons */
.btn-primary {
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  font-weight: 600;
  cursor: pointer;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  font-family: "Inter", sans-serif;
}
.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 20px rgba(249, 115, 22, 0.3);
}

.btn-secondary {
  background: var(--glass-bg);
  border: 1px solid var(--glass-border);
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  font-weight: 600;
  cursor: pointer;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
  font-family: "Inter", sans-serif;
}
.btn-secondary:hover {
  background: rgba(255, 255, 255, 0.1);
  transform: translateY(-2px);
}

.large {
  padding: 1rem 2.5rem;
  font-size: 1.1rem;
}

/* Hero Section */
.hero {
  min-height: 80vh;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 5%;
  position: relative;
  z-index: 10;
}

.hero-content {
  max-width: 600px;
}

.gradient-text {
  font-size: 5rem;
  line-height: 1.1;
  margin-bottom: 1.5rem;
  background: linear-gradient(to right, #fff, var(--text-secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle {
  font-size: 1.25rem;
  color: var(--text-secondary);
  margin-bottom: 2.5rem;
  max-width: 90%;
}

.cta-group {
  display: flex;
  gap: 1rem;
}

/* Hero Graphic */
.hero-graphic {
  position: relative;
  width: 500px;
  height: 500px;
}

.floating-shape {
  position: absolute;
  border-radius: 20px;
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.1),
    rgba(255, 255, 255, 0)
  );
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.18);
  box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
}

.shape-1 {
  width: 250px;
  height: 300px;
  top: 10%;
  left: 20%;
  animation: float 6s ease-in-out infinite;
  background: linear-gradient(
    135deg,
    rgba(249, 115, 22, 0.2),
    rgba(225, 29, 72, 0.1)
  );
}

.shape-2 {
  width: 200px;
  height: 200px;
  bottom: 20%;
  right: 10%;
  border-radius: 50%;
  animation: float 8s ease-in-out infinite reverse;
  background: linear-gradient(
    135deg,
    rgba(245, 158, 11, 0.2),
    rgba(249, 115, 22, 0.1)
  );
}

.shape-3 {
  width: 150px;
  height: 150px;
  top: 40%;
  left: -10%;
  border-radius: 30px;
  animation: float 7s ease-in-out infinite 1s;
  background: linear-gradient(
    135deg,
    rgba(190, 18, 60, 0.2),
    rgba(255, 255, 255, 0.05)
  );
  transform: rotate(45deg);
}

@keyframes float {
  0% {
    transform: translateY(0px) rotate(0deg);
  }
  50% {
    transform: translateY(-30px) rotate(5deg);
  }
  100% {
    transform: translateY(0px) rotate(0deg);
  }
}

/* About Section */
.about-section {
  padding: 5rem 5%;
  position: relative;
  z-index: 10;
  margin-top: 2rem;
}

.about-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.text-left {
  text-align: left;
  margin-bottom: 2rem;
}

.paragraph {
  color: var(--text-secondary);
  font-size: 1.1rem;
  margin-bottom: 1.5rem;
}

.about-action {
  margin-top: 2rem;
}

.about-stats {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
  padding: 3rem;
  border-radius: 24px;
  border: 1px solid var(--glass-border);
}

.stat-item h3 {
  font-size: 3rem;
  font-family: "Outfit", sans-serif;
  color: var(--primary);
  margin-bottom: 0.5rem;
}

.stat-item p {
  color: var(--text-secondary);
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  font-size: 0.9rem;
}

/* Common Section Styles */
.section-title {
  text-align: center;
  font-size: 3rem;
  margin-bottom: 4rem;
  background: linear-gradient(to right, #fff, var(--text-secondary));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Features */
.features {
  padding: 5rem 5%;
  position: relative;
  z-index: 10;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.feature-card {
  padding: 2.5rem;
  border-radius: 24px;
  background: var(--glass-bg);
  border: 1px solid var(--glass-border);
  backdrop-filter: blur(12px);
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease,
    border-color 0.3s ease;
  position: relative;
  overflow: hidden;
  text-align: center; /* Centering content and icons inside */
}

.feature-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.05) 0%,
    rgba(255, 255, 255, 0) 100%
  );
  opacity: 0;
  transition: opacity 0.3s ease;
  pointer-events: none;
}

.feature-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
  border-color: rgba(255, 255, 255, 0.2);
}

.feature-card:hover::before {
  opacity: 1;
}

.icon-wrapper {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.05);
  transition: transform 0.3s ease;
}

.feature-card:hover .icon-wrapper {
  transform: scale(1.1) rotate(5deg);
}

.icon-wrapper :deep(svg) {
  width: 2.2rem;
  height: 2.2rem;
  stroke: var(--primary);
  fill: none;
  stroke-width: 1.5;
}

.feature-card h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.feature-card p {
  color: var(--text-secondary);
}

/* Pricing Section */
.pricing {
  padding: 5rem 5%;
  position: relative;
  z-index: 10;
}

.pricing-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  align-items: center;
}

.pricing-card {
  padding: 3rem 2rem;
  border-radius: 24px;
  background: var(--glass-bg);
  border: 1px solid var(--glass-border);
  backdrop-filter: blur(12px);
  position: relative;
  transition: transform 0.3s ease;
}

.pricing-card:hover {
  transform: translateY(-5px);
}

.featured-plan {
  background: rgba(255, 255, 255, 0.06);
  border-color: var(--primary);
  transform: scale(1.05);
  box-shadow: 0 20px 40px rgba(249, 115, 22, 0.15);
}

.featured-plan:hover {
  transform: scale(1.05) translateY(-5px);
}

.popular-badge {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: var(--primary);
  color: white;
  font-size: 0.8rem;
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-weight: bold;
}

.pricing-card h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: var(--text-secondary);
}

.price {
  font-size: 3.5rem;
  font-family: "Outfit", sans-serif;
  font-weight: 800;
  margin-bottom: 2rem;
  color: var(--text-primary);
}

.features-list {
  list-style: none;
  margin-bottom: 2.5rem;
}

.features-list li {
  margin-bottom: 1rem;
  color: var(--text-secondary);
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.check {
  color: var(--primary);
  font-weight: bold;
}

/* Footer */
.footer {
  padding: 4rem 5% 2rem;
  border-top: 1px solid var(--glass-border);
  margin-top: 5rem;
  z-index: 10;
  position: relative;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2rem;
}

.social-links {
  display: flex;
  gap: 1.5rem;
}

.social-link {
  color: var(--text-secondary);
  text-decoration: none;
  transition: color 0.3s;
}

.social-link:hover {
  color: var(--primary);
}

.copyright {
  text-align: center;
  color: var(--text-secondary);
  font-size: 0.9rem;
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
}

/* Reveal Animations */
.reveal {
  opacity: 0;
  transition: all 1s cubic-bezier(0.16, 1, 0.3, 1);
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0) scale(1);
}

.fade-up {
  transform: translateY(50px);
}

.fade-down {
  transform: translateY(-50px);
}

.scale-up {
  transform: scale(0.9);
}

/* -----------------------------
   Responsive Medias
------------------------------ */
@media (max-width: 1024px) {
  .hero-graphic {
    width: 400px;
    height: 400px;
  }

  .about-container {
    gap: 2rem;
  }
}

@media (max-width: 968px) {
  .hero {
    flex-direction: column;
    text-align: center;
    padding-top: 6rem;
  }

  .hero-content {
    max-width: 100%;
  }

  .hero-graphic {
    width: 100%;
    margin-top: 3rem;
  }

  .cta-group {
    justify-content: center;
  }

  .subtitle {
    margin: 0 auto 2.5rem auto;
  }

  .about-container {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .text-left {
    text-align: center !important;
  }

  .featured-plan {
    transform: scale(1);
  }

  .featured-plan:hover {
    transform: translateY(-5px);
  }

  .about-stats {
    margin-top: 2rem;
  }
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
  }

  .logo {
    font-size: 1.5rem;
  }

  .navbar {
    padding: 1.5rem 5%;
  }

  .gradient-text {
    font-size: 3.5rem;
  }

  .subtitle {
    font-size: 1.1rem;
    max-width: 100%;
  }

  .cta-group {
    flex-direction: column;
    gap: 1rem;
  }

  .large {
    width: 100%;
    max-width: 300px;
    margin: 0 auto;
  }

  .hero-graphic {
    height: 350px;
  }

  .shape-1 {
    width: 180px;
    height: 220px;
    left: 10%;
  }
  .shape-2 {
    width: 150px;
    height: 150px;
    right: 5%;
  }
  .shape-3 {
    width: 100px;
    height: 100px;
  }

  .section-title {
    font-size: 2.5rem;
    margin-bottom: 3rem;
  }

  .about-section,
  .features,
  .pricing {
    padding: 4rem 5%;
    margin-top: 0;
  }

  .about-stats {
    grid-template-columns: 1fr;
    padding: 2rem;
  }

  .stat-item h3 {
    font-size: 2.5rem;
  }

  .features-grid {
    grid-template-columns: 1fr;
  }

  .pricing-grid {
    grid-template-columns: 1fr;
  }

  .footer-content {
    flex-direction: column;
    gap: 1.5rem;
    text-align: center;
  }

  .social-links {
    justify-content: center;
  }
}

@media (max-width: 480px) {
  .gradient-text {
    font-size: 2.8rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .feature-card {
    padding: 2rem 1.5rem;
  }

  .pricing-card {
    padding: 2.5rem 1.5rem;
  }

  .price {
    font-size: 2.8rem;
  }
}
</style>
