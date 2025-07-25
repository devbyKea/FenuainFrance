<template>

    <!-- Vague de transition (collée à la section précédente) -->
  <div class="wave-transition">
    <!-- Vague de fond intégrée directement -->
    <svg class="hero-wave" viewBox="0 0 1440 180" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
  <defs>
    <linearGradient id="heroGradient" x1="0%" y1="50%" x2="100%" y2="50%">
      <stop offset="0%" stop-color="#f7b500" />
      <stop offset="100%" stop-color="#fffaf4" />
    </linearGradient>
  </defs>
  <path
    :d="wavePath"
    fill="url(#heroGradient)"
    class="wave-animated"
  />
</svg>
  </div>
  <section class="about">
    <div class="about-content">
      <h2 class="about-title">🌴 À propos de moi</h2>
      <p class="about-text">
        Je m'appelle Keanu, je suis développeur web. Originaire de Tahiti, je suis arrivé en France en 2018 pour poursuivre mes études et construire ma vie ici.  
      </p>
      <p class="about-text">
        Les débuts n’ont pas été faciles : nouveau pays, pas de repères, peu de contacts, des démarches administratives complexes... J’ai souvent galéré à trouver un logement, à m’orienter ou simplement à me sentir chez moi.
      </p>
      <p class="about-text">
        Aujourd’hui, je veux transformer cette expérience en force 💪 et aider les personnes du fenua qui arrivent à Bordeaux à s’installer plus sereinement : infos pratiques, bons plans, liens utiles et entraide 🌺
      </p>
      <p class="about-text">
        Passionné par les sports de glisse 🛹🏄‍♂️ et la musique 🎸, je développe ce projet avec le cœur, en espérant qu’il puisse vraiment servir à d'autres 🤙
      </p>
      <div class="portfolio-link">
        <h3 class="portfolio-title">Mon Portfolio :</h3>
          <a href="https://www.devbykea.com" target="_blank" rel="noopener">
    <img src="/portfolio.png" alt="Mon portfolio" />
  </a>
</div>

    </div>

    
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Vague animée
const wavePath = ref('M0,160 C360,280 1080,0 1440,160 L1440,320 L0,320 Z')

const frames = [
  "M0,320L0,160C180,120,360,200,540,190C720,180,900,100,1080,130C1260,160,1350,200,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,140,320,180,480,200C640,220,800,140,960,130C1120,120,1280,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,180,360,220,540,180C720,140,900,100,1080,120C1260,140,1350,200,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,130,320,160,480,180C640,200,800,180,960,150C1120,120,1280,160,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,170,360,220,540,200C720,180,900,120,1080,130C1260,140,1350,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,160,320,200,480,190C640,180,800,120,960,140C1120,160,1280,200,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,130,360,160,540,200C720,240,900,200,1080,160C1260,120,1350,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,150,320,190,480,180C640,170,800,130,960,130C1120,130,1280,170,1440,160L1440,320L0,320Z",
  "M0,320L0,160C170,120,340,180,510,170C680,160,850,130,1020,140C1190,150,1315,190,1440,160L1440,320L0,320Z",
  "M0,320L0,160C150,130,300,170,450,200C600,230,750,180,900,150C1050,120,1200,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,160,360,210,540,190C720,170,900,110,1080,130C1260,150,1350,190,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,150,320,200,480,200C640,200,800,140,960,130C1120,120,1280,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C190,180,380,230,570,200C760,170,950,120,1140,140C1330,160,1385,200,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,140,320,180,480,190C640,200,800,150,960,140C1120,130,1280,170,1440,160L1440,320L0,320Z",
  "M0,320L0,160C170,110,340,160,510,180C680,200,850,160,1020,150C1190,140,1315,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C150,170,300,210,450,180C600,150,750,110,900,130C1050,150,1200,190,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,190,360,230,540,200C720,170,900,100,1080,120C1260,140,1350,190,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,160,320,200,480,200C640,200,800,130,960,140C1120,150,1280,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,120,360,180,540,190C720,200,900,140,1080,130C1260,120,1350,170,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,150,320,190,480,180C640,170,800,130,960,130C1120,130,1280,170,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,120,360,200,540,190C720,180,900,100,1080,130C1260,160,1350,200,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,140,320,180,480,200C640,220,800,140,960,130C1120,120,1280,180,1440,160L1440,320L0,320Z"
]



let i = 0

onMounted(() => {
  const isMobile = window.innerWidth < 768

  if (!isMobile) {
    const animate = () => {
      i = (i + 1) % frames.length
      wavePath.value = frames[i]
      setTimeout(() => {
        requestAnimationFrame(animate)
      }, 1200)
    }

    requestAnimationFrame(animate)
  }
})


</script>

<style scoped>
.about {
  position: relative;
  min-height: 40vh;
  padding: 6rem 2rem 6rem 2rem; /* top right bottom left */
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: url('/public/bg_about.jpg') no-repeat center center;
  background-size: 120%;
  background-attachment: fixed;
  font-family: 'Inter', sans-serif;
}

.about::after {
  content: "";
  position: absolute;
  bottom: -80px;   /* 📏 Dépasse de 80px sous le footer */
  left: 0;
  width: 100%;
  height: 100px;
  background: inherit; /* Reprend le fond de la section about */
  z-index: 0;
}


.about-content {
  padding: 2rem;
  border-radius: 20px;
  max-width: 600px;
  text-align: center;
}

.about-title {
  font-size: 2rem;
  font-weight: bold;
  color: #3e5f47;
  margin-bottom: 1rem;
}

.about-text {
  font-size: 1.1rem;
  color: #3e5f47;
  line-height: 1.6;
}

.portfolio-title {
  font-size: 1.2rem;
  font-weight: 600;
  color: #3e5f47; /* Vert foncé doux, harmonisé avec ton thème */
  margin-bottom: 0.8rem;
  text-align: center;
  font-family: 'Inter', sans-serif;
  padding: 0.4rem 1rem;
  border-radius: 12px;
  
}

.portfolio-link {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
}

.portfolio-link img {
  width: 300px;
  height: 150px;
  transition: transform 0.3s ease, opacity 0.3s ease;
  filter: drop-shadow(0 4px 12px rgba(0, 0, 0, 0.1));
}

.portfolio-link img:hover {
  transform: scale(1.08);
  opacity: 0.85;
}


.hero-wave {
  position: absolute;
  bottom: -1px;
  left: 0;
  width: 100%;
  height: 80px;
  z-index: -1;
  transition: d 1s ease-in-out;
}

.wave-animated {
  transition: d 1.5s ease-in-out;
}
.wave-transition {
  width: 100%;
  line-height: 0;
  position: relative;
  margin-top: -1px; /* évite ligne blanche entre les blocs */
  z-index: 1;
}


.wave-transition svg {
  display: block;
  width: 100%;
  height: auto;
}

.wave-path {
  animation: waveAnim 4s linear infinite;
}

@keyframes waveAnim {
  0% {
    d: path("M 0,600 L 0,225 C 79.1,194.7 158.2,164.4 269,184 C 379.7,203.5 522.0,273.0 621,291 C 719.9,308.9 775.3,275.2 859,257 C 942.6,238.7 1054.4,235.7 1156,233 C 1257.5,230.2 1348.7,227.6 1440,225 L 1440,600 L 0,600 Z");
  }
  50% {
    d: path("M 0,600 L 0,225 C 105.2,206.7 210.4,188.4 315,194 C 419.5,199.5 523.2,229.0 619,230 C 714.7,230.9 802.3,203.2 879,191 C 955.6,178.7 1021.3,181.7 1113,190 C 1204.6,198.2 1322.3,211.6 1440,225 L 1440,600 L 0,600 Z");
  }
  100% {
    d: path("M 0,600 L 0,225 C 79.1,194.7 158.2,164.4 269,184 C 379.7,203.5 522.0,273.0 621,291 C 719.9,308.9 775.3,275.2 859,257 C 942.6,238.7 1054.4,235.7 1156,233 C 1257.5,230.2 1348.7,227.6 1440,225 L 1440,600 L 0,600 Z");
  }
}


/* Pour les écrans <= 780px */
@media (max-width: 780px) {
  .about {
    background-image: none;
    background-color: #fffaf4; /* ou une autre couleur claire de ton thème */
    background-attachment: scroll; /* pour éviter tout bug de scroll */
  }

  .about-content {
    max-width: 95%;
    padding: 1rem;
  }

  .about-title {
    font-size: 1.4rem;
  }

  .about-text {
    font-size: 0.95rem;
    line-height: 1.5;
  }

  .portfolio-link img {
    width: 100%;
    max-width: 250px;
  }
}

</style>
