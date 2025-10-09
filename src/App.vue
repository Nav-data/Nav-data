<template>
  <div class="app" :data-theme="theme">
    <!-- Fixed Header Navigation -->
    <header class="header" :class="{ 'scrolled': isScrolled }">
      <nav class="nav-container">
        <a href="#" class="logo">
          <span class="sr-only">Nav-data</span>
          <span aria-hidden="true">NAV-DATA</span>
        </a>
        <div class="nav-right">
          <ul class="nav-links">
            <li><a href="#about" class="nav-link">About</a></li>
            <li><a href="#aircraft" class="nav-link">Developers</a></li>
            <li><a href="https://github.com" target="_blank" rel="noopener noreferrer" class="nav-link">GitHub</a></li>
          </ul>
          <button @click="toggleTheme" class="theme-toggle" :aria-label="theme === 'dark' ? 'Switch to light mode' : 'Switch to dark mode'">
            <svg v-if="theme === 'dark'" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="12" cy="12" r="5"/>
              <line x1="12" y1="1" x2="12" y2="3"/>
              <line x1="12" y1="21" x2="12" y2="23"/>
              <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/>
              <line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
              <line x1="1" y1="12" x2="3" y2="12"/>
              <line x1="21" y1="12" x2="23" y2="12"/>
              <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/>
              <line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
            </svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
            </svg>
          </button>
        </div>
      </nav>
    </header>

    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-overlay"></div>
      <div class="hero-background">
        <img 
          src="/aircraft-hero.jpg" 
          alt="Aviation aircraft" 
          class="hero-image"
          @error="handleImageError"
        />
      </div>
      <div class="hero-content">
        <div class="hero-text fade-in-up">
          <h1 class="hero-title">NAV-DATA</h1>
          <div class="hero-divider"></div>
          <p class="hero-subtitle">Your Gateway to Aviation</p>
          <p class="hero-description">
            Explore the world of flight simulation with comprehensive resources, 
            navigation data, and tools for virtual pilots of all skill levels.
          </p>
          <div class="hero-cta">
            <a href="#about" class="cta-button">Learn More</a>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section class="about-section" id="about">
      <div class="container">
        <div class="about-content fade-in">
          <div class="about-header">
            <span class="section-label">About</span>
            <h2 class="section-title">Welcome to Nav-data</h2>
            <div class="section-divider"></div>
          </div>
          
          <div class="about-intro">
            <p class="about-text-large">
              We're a passionate community of aviation enthusiasts dedicated to creating 
              high-quality data converters for flight simulation platforms. Our mission 
              is to bridge the gap between different aircraft systems and flight simulators 
              by developing robust data conversion tools.
            </p>
          </div>

          <div class="about-details">
            <div class="about-section-block">
              <h3 class="about-subtitle">What We Do</h3>
              <p class="about-text">
                We specialize in converting navigation and aircraft data between various 
                formats and platforms, ensuring compatibility across different flight 
                simulation ecosystems. Our converters help pilots and aviation enthusiasts 
                seamlessly transfer data between:
              </p>
              <ul class="about-list">
                <li>Flight management systems</li>
                <li>Navigation databases</li>
                <li>Chart formats</li>
                <li>Aircraft-specific data structures</li>
              </ul>
            </div>

            <div class="about-section-block">
              <h3 class="about-subtitle">Supported Data Standards</h3>
              <ul class="about-list">
                <li><strong>ARINC 424</strong> - Industry standard for navigation data</li>
                <li><strong>Custom Formats</strong> - Proprietary aircraft-specific formats</li>
                <li><strong>Chart Data</strong> - Various aviation chart formats</li>
              </ul>
            </div>

            <div class="about-section-block">
              <h3 class="about-subtitle">Get Involved</h3>
              <p class="about-text">
                We love contributors! If you're interested in joining our community:
              </p>
              <ul class="about-list">
                <li>Send an email to <a href="mailto:epa6643@gmail.com" class="about-link">epa6643@gmail.com</a></li>
                <li>Include details about what you have and what you can provide</li>
                <li>Specify your area of expertise (data formats, specific aircraft, programming)</li>
              </ul>
            </div>

            <div class="about-section-block">
              <h3 class="about-subtitle">Project Status</h3>
              <p class="about-text">
                This project is actively maintained and continuously expanding. We regularly 
                add support for new aircraft and data formats based on community feedback 
                and industry developments.
              </p>
            </div>
          </div>

          <div class="about-cta">
            <a href="mailto:epa6643@gmail.com" class="cta-button">Contact Us</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Aircraft Section -->
    <section class="aircraft-section" id="aircraft">
      <div class="container">
        <div class="section-header fade-in">
          <span class="section-label">Supported</span>
          <h2 class="section-title">Aircraft Developers</h2>
          <div class="section-divider"></div>
        </div>
        <div class="aircraft-grid">
          <a 
            v-for="(aircraft, index) in aircraftList" 
            :key="aircraft.id"
            :href="aircraft.url"
            class="aircraft-card slide-in"
            :style="{ animationDelay: `${index * 150}ms` }"
            target="_blank"
            rel="noopener noreferrer"
          >
            <div class="aircraft-image">
              <div class="aircraft-placeholder">
                <img 
                  v-if="aircraft.logo" 
                  :src="aircraft.logo" 
                  :alt="aircraft.name + ' logo'"
                  class="aircraft-logo"
                  @error="handleImageError"
                />
                <IconTools v-else class="aircraft-icon" />
              </div>
            </div>
            <div class="aircraft-info">
              <h3 class="aircraft-name">{{ aircraft.name }}</h3>
              <p class="aircraft-type">{{ aircraft.type }}</p>
              <p class="aircraft-description">{{ aircraft.description }}</p>
            </div>
          </a>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <div class="footer-grid">
          <div class="footer-col">
            <h3 class="footer-logo">NAV-DATA</h3>
            <p class="footer-tagline">
              Elevating your aviation experience
            </p>
          </div>
          <div class="footer-col">
            <h4 class="footer-heading">Quick Links</h4>
            <ul class="footer-links">
              <li><a href="#about" class="footer-link">About</a></li>
              <li><a href="#aircraft" class="footer-link">Developers</a></li>
              <li><a href="mailto:epa6643@gmail.com" class="footer-link">Contact</a></li>
            </ul>
          </div>
          <div class="footer-col">
            <h4 class="footer-heading">Connect</h4>
            <div class="footer-social">
              <a href="https://github.com" target="_blank" rel="noopener noreferrer" class="footer-social-link">
                <span class="sr-only">GitHub</span>
                <svg class="footer-social-icon" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 0C4.477 0 0 4.484 0 10.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0110 4.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.203 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.942.359.31.678.921.678 1.856 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0020 10.017C20 4.484 15.522 0 10 0z" clip-rule="evenodd" />
                </svg>
              </a>
            </div>
            <p class="footer-copyright">&copy; {{ currentYear }} Nav-data</p>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import IconTools from './components/IconTools.vue'

const currentYear = computed(() => new Date().getFullYear())
const theme = ref('dark')
const isScrolled = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > window.innerHeight * 0.8
}

onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  if (savedTheme) {
    theme.value = savedTheme
  } else if (window.matchMedia && window.matchMedia('(prefers-color-scheme: light)').matches) {
    theme.value = 'light'
  }

  window.addEventListener('scroll', handleScroll)
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const toggleTheme = () => {
  theme.value = theme.value === 'dark' ? 'light' : 'dark'
  localStorage.setItem('theme', theme.value)
}

const handleImageError = (e) => {
  e.target.style.display = 'none'
}

const aircraftList = [
  {
    id: 1,
    name: 'iniBuilds',
    type: 'Aircraft Developer',
    description: 'High-fidelity aircraft systems',
    url: 'https://inibuilds.com/',
    logo: '/iniBuilds.png'
  },
  {
    id: 2,
    name: 'PMDG',
    type: 'Aircraft Developer',
    description: 'Professional flight simulation aircraft',
    url: 'https://pmdg.com/',
    logo: '/PMDG.png'
  },
  {
    id: 3,
    name: 'Fenix Simulations',
    type: 'Aircraft Developer',
    description: 'Advanced Airbus simulations',
    url: 'https://fenixsim.com/',
    logo: '/Fenix.png'
  },
  {
    id: 4,
    name: 'TFDI Design',
    type: 'Aircraft Developer',
    description: 'Detailed regional aircraft',
    url: 'https://tfdidesign.com/',
    logo: '/TFDI.png'
  },
  {
    id: 5,
    name: 'iFly',
    type: 'Aircraft Developer',
    description: 'Professional aircraft simulations',
    url: 'https://www.ifly.com/',
    logo: '/iFly.png'
  },
  {
    id: 6,
    name: 'X-Plane',
    type: 'Flight Simulator',
    description: 'Default and third-party aircraft',
    url: 'https://www.x-plane.com/',
    logo: '/X-Plane.png'
  }
]
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  min-height: 100vh;
  background-color: rgb(var(--background-rgb));
  color: rgb(var(--foreground-rgb));
  transition: background-color 0.3s ease, color 0.3s ease;
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}

/* Header */
.header {
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 20;
  padding: 1.25rem 1.5rem;
  transition: all 0.3s ease;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.9) 0%, rgba(0, 0, 0, 0) 100%);
}

[data-theme="light"] .header.scrolled {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.nav-container {
  max-width: 80rem;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-right {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.logo {
  font-size: 1.25rem;
  font-weight: 300;
  letter-spacing: 0.15em;
  color: #ffffff;
  text-decoration: none;
  transition: color 0.3s ease;
}

[data-theme="light"] .header.scrolled .logo {
  color: rgb(var(--foreground-rgb));
}

.logo:hover {
  color: rgb(var(--accent-color));
}

.nav-links {
  display: flex;
  gap: 2.5rem;
  list-style: none;
  font-size: 0.875rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.nav-link {
  opacity: 0.8;
  color: #ffffff;
  text-decoration: none;
  transition: opacity 0.3s ease, color 0.3s ease;
  position: relative;
  padding: 0.25rem 0;
}

[data-theme="light"] .header.scrolled .nav-link {
  color: rgb(var(--foreground-rgb));
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background-color: rgb(var(--accent-color));
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.3s ease;
}

.nav-link:hover {
  opacity: 1;
  color: rgb(var(--accent-color));
}

.nav-link:hover::after {
  transform: scaleX(1);
  transform-origin: left;
}

.theme-toggle {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0.5rem;
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 0.25rem;
  color: #ffffff;
  cursor: pointer;
  transition: all 0.3s ease;
}

[data-theme="light"] .header.scrolled .theme-toggle {
  border-color: rgba(var(--foreground-rgb), 0.2);
  color: rgb(var(--foreground-rgb));
}

.theme-toggle:hover {
  border-color: rgba(var(--accent-color), 0.7);
  background: rgba(var(--accent-color), 0.1);
}

/* Hero Section */
.hero {
  position: relative;
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.hero-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
}

.hero-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  transform: scale(1.02);
  transition: transform 30s ease;
}

.hero:hover .hero-image {
  transform: scale(1);
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.7) 0%,
    rgba(0, 0, 0, 0.5) 50%,
    rgba(0, 0, 0, 0.7) 100%
  );
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  max-width: 56rem;
  padding: 0 1.5rem;
  text-align: center;
  width: 100%;
}

.hero-title {
  font-size: 4.5rem;
  font-weight: 200;
  letter-spacing: 0.2em;
  margin-bottom: 1.5rem;
  line-height: 1;
  color: #ffffff;
}

.hero-divider {
  height: 1px;
  width: 5rem;
  background: rgba(255, 255, 255, 0.6);
  margin: 1.5rem auto;
}

.hero-subtitle {
  font-size: 1.25rem;
  font-weight: 300;
  margin-bottom: 1rem;
  opacity: 0.8;
  letter-spacing: 0.05em;
  color: #ffffff;
}

.hero-description {
  font-size: 1rem;
  line-height: 1.75;
  margin-bottom: 2.5rem;
  opacity: 0.8;
  max-width: 42rem;
  margin-left: auto;
  margin-right: auto;
  color: #ffffff;
}

.hero-cta {
  display: flex;
  justify-content: center;
  margin-top: 2.5rem;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  padding: 0.75rem 2rem;
  font-size: 0.875rem;
  font-weight: 400;
  text-decoration: none;
  border: 1px solid rgba(255, 255, 255, 0.3);
  color: #ffffff;
  background-color: transparent;
  transition: all 0.3s ease;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

.cta-button:hover {
  background-color: rgba(255, 255, 255, 0.1);
  border-color: rgb(var(--accent-color));
}

/* Container */
.container {
  max-width: 80rem;
  margin: 0 auto;
  padding: 0 1.5rem;
}

/* Section Styles */
.aircraft-section {
  padding: 8rem 0;
  background-color: rgb(var(--background-rgb));
  transition: background-color 0.3s ease;
}

.about-section {
  padding: 8rem 0;
  background-color: rgb(var(--background-secondary-rgb));
  position: relative;
  transition: background-color 0.3s ease;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-label {
  color: rgba(var(--accent-color), 0.8);
  text-transform: uppercase;
  letter-spacing: 0.2em;
  font-size: 0.75rem;
  opacity: 0.8;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 300;
  letter-spacing: 0.1em;
  margin-top: 0.5rem;
}

.section-divider {
  height: 1px;
  width: 3rem;
  background: rgba(var(--foreground-rgb), 0.2);
  margin: 1.5rem auto 0;
  transition: background 0.3s ease;
}

/* Aircraft Grid */
.aircraft-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2.5rem;
}

.aircraft-card {
  display: block;
  text-decoration: none;
  color: inherit;
  background: rgba(var(--foreground-rgb), 0.03);
  border: 1px solid rgba(var(--foreground-rgb), 0.1);
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.22, 1, 0.36, 1);
  cursor: pointer;
}

.aircraft-card:hover {
  transform: translateY(-6px);
  border-color: rgba(var(--accent-color), 0.3);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

.aircraft-image {
  aspect-ratio: 16 / 9;
  overflow: hidden;
  background: linear-gradient(135deg, rgba(var(--foreground-rgb), 0.05) 0%, rgba(var(--foreground-rgb), 0.02) 100%);
}

.aircraft-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, rgba(var(--accent-color), 0.1) 0%, rgba(var(--accent-color), 0.05) 100%);
}

.aircraft-icon {
  width: 5rem;
  height: 5rem;
  color: rgba(var(--accent-color), 0.4);
  transition: all 0.5s ease;
}

.aircraft-card:hover .aircraft-icon {
  transform: scale(1.1);
  color: rgba(var(--accent-color), 0.7);
}

.aircraft-logo {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: all 0.5s ease;
}

.aircraft-card:hover .aircraft-logo {
  transform: scale(1.02);
}

.aircraft-info {
  padding: 1.5rem;
}

.aircraft-name {
  font-size: 1.25rem;
  font-weight: 400;
  letter-spacing: 0.05em;
  margin-bottom: 0.5rem;
}

.aircraft-type {
  font-size: 0.875rem;
  color: rgba(var(--accent-color), 0.8);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-bottom: 1rem;
}

.aircraft-description {
  font-size: 0.875rem;
  opacity: 0.7;
  line-height: 1.6;
}

/* About Section */
.about-content {
  max-width: 60rem;
  margin: 0 auto;
}

.about-header {
  text-align: center;
  margin-bottom: 3rem;
}

.about-intro {
  text-align: center;
  margin-bottom: 4rem;
}

.about-text-large {
  font-size: 1.125rem;
  line-height: 1.8;
  opacity: 0.8;
  max-width: 48rem;
  margin: 0 auto;
}

.about-details {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 3rem;
  margin-bottom: 4rem;
}

.about-section-block {
  text-align: left;
}

.about-subtitle {
  font-size: 1.25rem;
  font-weight: 400;
  letter-spacing: 0.05em;
  margin-bottom: 1rem;
  color: rgb(var(--accent-color));
}

.about-text {
  font-size: 0.95rem;
  line-height: 1.8;
  opacity: 0.7;
  margin-bottom: 1rem;
}

.about-list {
  list-style: none;
  padding-left: 0;
  margin-top: 1rem;
}

.about-list li {
  font-size: 0.95rem;
  line-height: 1.8;
  opacity: 0.7;
  padding-left: 1.5rem;
  position: relative;
  margin-bottom: 0.5rem;
}

.about-list li::before {
  content: '→';
  position: absolute;
  left: 0;
  color: rgb(var(--accent-color));
  opacity: 0.6;
}

.about-link {
  color: rgb(var(--accent-color));
  text-decoration: none;
  transition: opacity 0.3s ease;
}

.about-link:hover {
  opacity: 1;
  text-decoration: underline;
}

.about-cta {
  text-align: center;
  margin-top: 3rem;
}

/* Footer */
.footer {
  background-color: rgb(var(--background-rgb));
  border-top: 1px solid rgba(var(--foreground-rgb), 0.05);
  padding: 3rem 1.5rem;
  transition: background-color 0.3s ease, border-color 0.3s ease;
}

.footer-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  max-width: 80rem;
  margin: 0 auto;
}

.footer-col {
  display: flex;
  flex-direction: column;
}

.footer-logo {
  font-size: 1.125rem;
  letter-spacing: 0.2em;
  margin-bottom: 1rem;
  color: rgb(var(--accent-color));
  font-weight: 300;
}

.footer-tagline {
  font-size: 0.875rem;
  opacity: 0.6;
  line-height: 1.6;
  max-width: 20rem;
}

.footer-heading {
  font-size: 0.875rem;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  margin-bottom: 1rem;
  opacity: 0.8;
  font-weight: 400;
}

.footer-links {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.footer-link {
  font-size: 0.875rem;
  opacity: 0.6;
  color: rgb(var(--foreground-rgb));
  text-decoration: none;
  transition: all 0.3s ease;
}

.footer-link:hover {
  opacity: 1;
  color: rgb(var(--accent-color));
}

.footer-social {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.footer-social-link {
  opacity: 0.6;
  color: rgb(var(--foreground-rgb));
  transition: all 0.3s ease;
}

.footer-social-link:hover {
  opacity: 1;
  color: rgb(var(--accent-color));
}

.footer-social-icon {
  width: 1.25rem;
  height: 1.25rem;
}

.footer-copyright {
  font-size: 0.875rem;
  opacity: 0.4;
  margin-top: 1.5rem;
}

/* Responsive */
@media (max-width: 768px) {
  .nav-right {
    gap: 1rem;
  }

  .nav-links {
    gap: 1.5rem;
    font-size: 0.75rem;
  }

  .hero-title {
    font-size: 2.5rem;
    letter-spacing: 0.15em;
  }

  .hero-subtitle {
    font-size: 1rem;
  }

  .hero-description {
    font-size: 0.875rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .aircraft-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .about-details {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .footer-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .header {
    padding: 1rem 1rem;
  }

  .nav-right {
    gap: 0.75rem;
  }

  .nav-links {
    gap: 0.75rem;
  }

  .nav-link {
    font-size: 0.7rem;
  }

  .theme-toggle {
    padding: 0.4rem;
  }

  .theme-toggle svg {
    width: 16px;
    height: 16px;
  }

  .hero-title {
    font-size: 2rem;
  }

  .section-title {
    font-size: 1.5rem;
  }
}
</style>

