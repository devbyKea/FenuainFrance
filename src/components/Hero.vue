<template>
  <section class="hero">
    <div class="hero-inner">
      <div class="hero-card">
        <h1><span>Ia ora na ☀️</span><br />Bienvenue en France</h1>
        <p>
          Tu viens du fenua ? Ce site est là pour t'aider à t'installer,
          trouver les bonnes infos et t'accompagner.
        </p>
        <a href="#aides" class="hero-button">Découvrir les aides</a>
      </div>
    </div>

    <!-- Vague de fond intégrée directement -->
    <svg class="hero-wave" viewBox="0 0 1440 320" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
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

  </section>
</template>



<script setup lang="ts">
import { ref, onMounted } from 'vue'

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
.hero {
  background:
    linear-gradient(to right, rgba(255, 255, 255, 0.85) 0%, rgba(255, 255, 255, 0) 60%),
    url('/bg_hero.JPG') no-repeat center / cover;
  background-attachment: fixed;
  font-family: 'Inter', sans-serif;
  min-height: 100vh;
  padding: 2rem;
  padding-top: 160px;
  position: relative; /* nécessaire pour que le SVG se positionne correctement */
  overflow: hidden;
  z-index: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}

.hero-inner {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 0 2rem;
}

.hero-card {
    background: linear-gradient(
    to right,
    rgba(255, 255, 255, 0.35),
    rgba(255, 255, 255, 0.25)
  );
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);

  border-radius: 100px;
  padding: 2rem;
  max-width: 90vw;

  /* Néomorphisme soft */
  box-shadow:
    10px 10px 30px rgba(0, 0, 0, 0.1),   /* ombre projetée */
    -10px -10px 30px rgba(255, 255, 255, 0.3); /* lumière douce */

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  gap: 1.5rem;
  transition: all 0.3s ease;
  margin-top: -10rem;

}

.hero-card h1 {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 3rem;
  font-weight: 700;
  color: #f7b500;
  line-height: 1.2;
  margin: 0;
}

.hero-card h1 span {
  color: #3e5f47;
}

.hero-card p {
  font-size: 1.1rem;
  color: #3e5f47;
  margin: 0;
}

.hero-button {
  position: relative;
  display: inline-block;
  padding: 0.8rem 1.5rem;
  background-color: #f7b500;
  color: #fff;
  border: none;
  border-radius: 50px;
  font-weight: 600;
  text-decoration: none;
  width: fit-content;
  overflow: hidden;
  transition: background-color 0.3s ease, transform 0.3s ease;
  animation: pulse-shine 3s infinite ease-in-out;
}

.hero-button:hover {
  background-color: #d99a00;
  transform: scale(1.03);
  animation: none;
}

.hero-button::before {
  content: "";
  position: absolute;
  top: 0;
  left: -75%;
  width: 50%;
  height: 100%;
  background: linear-gradient(
    120deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.4) 50%,
    rgba(255, 255, 255, 0) 100%
  );
  transform: skewX(-20deg);
  pointer-events: none;
}

.hero-button:hover::before {
  animation: shine 1s ease forwards;
}

@keyframes pulse-shine {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.015);
  }
  100% {
    transform: scale(1);
  }
}

@keyframes shine {
  0% {
    left: -75%;
  }
  100% {
    left: 125%;
  }
}
.hero-wave {
  position: absolute;
  bottom: -1px;
  left: 0;
  width: 100%;
  height: 100px;
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




@media screen and (max-width: 768px) {
  .hero {
    background-attachment: scroll !important;
    background-position: center top !important;
    background-size: cover !important;
  }

  .hero .glass {
    max-width: 70%;
    margin: 0 auto;
  }
}

@media screen and (max-width: 480px) {
  .hero-card h1 {
    font-size: 1.8rem;
    line-height: 2.2rem;
  }

  .hero-card h2 {
    font-size: 1.4rem;
    line-height: 2rem;
  }

  .hero-card p {
    font-size: 0.95rem;
  }

  .hero-button {
    font-size: 1rem;
    padding: 0.6rem 1.2rem;
  }
}

</style>
