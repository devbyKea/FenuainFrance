<template>

  <!-- Vague de transition (collée à la section précédente) -->
  <div class="wave-transition">
    <svg class="hero-wave" viewBox="0 0 1440 220" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
      <defs>
<linearGradient id="heroGradient" x1="0%" y1="0%" x2="100%" y2="0%">
  <stop offset="0%" stop-color="#fffaf4" />
  <stop offset="100%" stop-color="#f7b500" />
</linearGradient>
      </defs>
      <path
        :d="wavePath"
        fill="url(#heroGradient)"
        class="wave-animated"
      />
    </svg>
  </div>

  <section class="socials">
    <h2 class="title">Réseaux et partenaires</h2>
    <div class="icons">
      <a
        v-for="(social, index) in socialLinks"
        :key="index"
        :href="social.url"
        target="_blank"
        rel="noopener"
        :aria-label="social.name"
        class="icon"
      >
        <img :src="social.icon" :alt="social.name" />
      </a>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface SocialLink {
  name: string
  url: string
  icon: string
}

const socialLinks: SocialLink[] = [
  {
    name: 'Page Facebook',
    url: 'https://www.facebook.com/profile.php?id=61578310214884',
    icon: '/icons/logo.png'
  },
  {
    name: 'Groupe Facebook',
    url: 'https://www.facebook.com/groups/1377063200036931/?notif_id=1753386482984510&notif_t=group_milestone&ref=notif',
    icon: '/icons/groupe.png'
  },
  {
    name: 'Groupe Facebook Logement',
    url: 'https://www.facebook.com/groups/821026889977086',
    icon: '/icons/groupe_log.png'
  }
]
// Vague animée
const wavePath = ref('M0,50 C360,280 1080,20 1440,50 L1440,100 L0,100 Z')

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
  "M0,320L0,160C160,140,320,180,480,200C640,220,800,140,960,130C1120,120,1280,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C160,140,320,180,480,200C640,220,800,140,960,130C1120,120,1280,180,1440,160L1440,320L0,320Z",
  "M0,320L0,160C180,120,360,200,540,190C720,180,900,100,1080,130C1260,160,1350,200,1440,160L1440,320L0,320Z"
]



let i = 0

onMounted(() => {
  const animate = () => {
    i = (i + 1) % frames.length
    wavePath.value = frames[i]
    setTimeout(() => {
      requestAnimationFrame(animate)
    }, 1200)
  }

  requestAnimationFrame(animate)
})

</script>

<style scoped>
.socials {
  text-align: center;
  padding: 4rem 2rem;
  background: url('/public/bg_socials.jpg') no-repeat center center;
  min-height: 50vh;
  background-size: cover;
  font-family: 'Inter', sans-serif;
}

.title {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 2rem;
  color: #3e5f47;
}

.icons {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.icon {
  display: inline-block;
  width: 200px;
  height: 200px;
  transition: transform 0.3s ease, opacity 0.3s ease;
}

.icon img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.icon:hover {
  transform: scale(1.1);
  opacity: 0.8;
}

.wave-transition {
  margin-top: -22rem; /* colle parfaitement */
  margin-bottom: 0rem;
  line-height: 0;
  height: auto;
  overflow: hidden;
  position: relative;
  z-index: 1;
}



.hero-wave {
  display: block;
  width: 100%;
  height: 100px;
  margin: 0;
}


.wave-animated {
  transition: d 1s ease-in-out;
}

@media screen and (max-width: 768px) {
  .socials {
    background-attachment: scroll !important;
    background-position: center top !important;
    background-size: cover !important;
  }

}
</style>
