<template>
  <Header />
  <Hero />
<div id="aides" class="no-spacing"><Aides /></div>
<div id="contact" class="no-spacing"><Contact /></div>

  <section id="socials"><Socials /></section>
  <section id="about"><About /></section>
  <Footer />
</template>


<script setup lang="ts">
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Aides from './components/Aides.vue'
import Contact from './components/Contact.vue'
import Socials from './components/Socials.vue'
import About from './components/About.vue'
import Footer from './components/Footer.vue'
</script>

<style scoped>

#socials {
  scroll-margin-top: 40rem; /* ajuste selon la hauteur de ton header */
}

main {
  padding: 2rem;
}
.hero {
  margin-bottom: 0;
}

.aides {
  margin-top: 0;
  margin-bottom: 0;
}

.socials {
  margin-top: 0;
  margin-bottom: 0;
}

.no-spacing {
  margin: 0;
  padding: 0;
}



</style>

