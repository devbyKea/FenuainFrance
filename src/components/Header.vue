<template>
  <header :class="['hero-nav', { hidden: !isVisible, scrolled: hasScrolled }]">

    <div class="nav-inner">
      <div class="logo">
        <a href="#top">
          <img src="/logo.png" alt="Logo Fenua in France" class="logo-img" />
        </a>
      </div>

      <!-- Desktop Navigation -->
<nav class="desktop-nav">
  <ul>
    <li><a href="#aides" class="nav-button">Aides</a></li>
    <li><a href="#contact" class="nav-button">Contact</a></li>
    <li><a href="#socials" class="nav-button">Socials</a></li>
    <li><a href="#about" class="nav-button">À propos</a></li>
  </ul>
</nav>

      <!-- Burger -->
      <div class="burger" @click="toggleMenu">
        <span :class="{ open: isOpen }"></span>
        <span :class="{ open: isOpen }"></span>
        <span :class="{ open: isOpen }"></span>
      </div>
    </div>

    <!-- Menu mobile -->
    <div :class="['mobile-menu', { closing: isClosing }]" v-if="isOpen || isClosing">
      <ul>
        <li><a href="#aides" @click="closeMenu">Aides</a></li>
        <li><a href="#contact" @click="closeMenu">Contact</a></li>
        <li><a href="#socials" @click="closeMenu">Socials</a></li>
        <li><a href="#about" @click="closeMenu">À propos</a></li>
      </ul>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isOpen = ref(false)
const isClosing = ref(false)
const isVisible = ref(true)
const hasScrolled = ref(false)

let lastScrollY = window.scrollY

// Gère l'ouverture / fermeture avec animation
const toggleMenu = () => {
  if (isOpen.value) {
    isClosing.value = true
    setTimeout(() => {
      isOpen.value = false
      isClosing.value = false
    }, 300) // Durée identique à l'animation CSS
  } else {
    isOpen.value = true
  }
}

const closeMenu = () => {
  isClosing.value = true
  setTimeout(() => {
    isOpen.value = false
    isClosing.value = false
  }, 300)
}

// Gère l’apparition / disparition de la navbar selon scroll direction
const handleScroll = () => {
  const currentScrollY = window.scrollY

  isVisible.value = currentScrollY < lastScrollY || currentScrollY < 10
  hasScrolled.value = currentScrollY > 10

  lastScrollY = currentScrollY
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>


<style scoped>
.hero-nav {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 999;
  padding: 1rem 0;
  background: transparent;
  transition: background-color 0.3s ease, backdrop-filter 0.3s ease, transform 0.3s ease;
}

.hero-nav.scrolled {
  background-color: rgba(255, 255, 255, 0.6);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.3);
}

.hero-nav.hidden {
  transform: translateY(-100%);
}


.nav-inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo-img {
  height: 60px;
  width: auto;
  cursor: pointer;
}

.desktop-nav ul {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

.desktop-nav a {
  font-weight: 1000;
  text-decoration: none;
  color: #fff;
  transition: color 0.3s ease;
}

.nav-button {
  display: inline-block;
  padding: 0.8rem 1.5rem;
  background-color: #f7b500;
  color: #fff;
  border: none;
  border-radius: 50px;
  font-weight: 600;
  text-decoration: none;
  transition: background-color 0.3s ease;
  width: fit-content;
}

.nav-button:hover {
  background-color: #d99a00;
}
/* Burger menu */
.burger {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 6px;
  cursor: pointer;
  z-index: 1001;
}

.burger span {
  width: 28px;
  height: 3px;
  background-color: #f7b500;
  border-radius: 2px;
  transition: all 0.4s ease;
  transform-origin: center;
}

/* Animation vers croix */
.burger span.open:nth-child(1) {
  transform: rotate(45deg) translateY(8px);
}

.burger span.open:nth-child(2) {
  opacity: 0;
}

.burger span.open:nth-child(3) {
  transform: rotate(-45deg) translateY(-8px);
}


/* Menu mobile */
.mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  z-index: 1000;
  animation: slideDown 0.3s ease forwards;
}

.mobile-menu.closing {
  animation: slideUp 0.3s ease forwards;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideUp {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0;
    transform: translateY(-20px);
  }
}


.mobile-menu ul {
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: center;
}

.mobile-menu li {
  margin: 1rem 0;
}

.mobile-menu a {
  font-size: 1.5rem;
  font-weight: 700;
  color: #3e5f47;
  text-decoration: none;
  transition: color 0.3s ease;
}

.mobile-menu a:hover {
  color: #f7b500;
}


/* ✅ Responsive burger */
@media (max-width: 768px) {
  .burger {
    display: flex;
  }

  .desktop-nav {
    display: none;
  }
}

</style>
