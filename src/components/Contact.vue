<template>
  <!-- Vague de transition (collée à la section précédente) -->
  <div class="wave-transition">
    <svg class="hero-wave" viewBox="0 0 1440 320" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">

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

  <section class="contact">
    <div class="glass-form">
      <h2 class="contact-title">📩 Contacte-moi</h2>
      <p class="contact-intro">
        Une question, une remarque ou une envie de collaborer ?
        N'hésite pas à m'écrire, je réponds toujours avec plaisir. 😊
      </p>
      <form @submit.prevent="sendEmail" class="flex flex-col">
        <div class="form-group">
          <label for="name">Nom</label>
          <input type="text" v-model="name" id="name" required />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input type="email" v-model="email" id="email" required />
        </div>
        <div class="form-group">
          <label for="objet">Objet</label>
          <input type="text" v-model="objet" id="objet" required />
        </div>        
        <div class="form-group">
          <label for="message">Message</label>
          <textarea v-model="message" id="message" rows="5" required></textarea>
        </div>
        <button type="submit" class="button">Envoyer</button>

      </form>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const name = ref('')
const email = ref('')
const objet = ref('')
const message = ref('')
const sendEmail = () => {
  console.log('Formulaire prêt à être envoyé avec EmailJS')
}

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
  setInterval(() => {
    i = (i + 1) % frames.length
    wavePath.value = frames[i]
  }, 1200) // toutes les 1200ms
})
</script>


<style scoped>
.contact {
  min-height: 100vh;
  padding: 1rem 2rem 6rem 2rem; /* ancien : 2rem 2rem 6rem 2rem */
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Inter', sans-serif;
  background: url('/bg_contact.jpg') no-repeat center center;
  background-size: cover;
  background-attachment: fixed;
}

.glass-form {
  margin-top: 0;
  margin-bottom: 12rem;
  background: rgba(255, 255, 255, 0.25);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  padding: 2rem;
  border-radius: 20px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 500px;
}

.contact-title {
  font-size: 2rem;
  text-align: center;
  font-weight: bold;
  margin-bottom: 1rem;
  color: #3e5f47;
}

.contact-intro {
  font-size: 1.1rem;
  color: #3e5f47;
  margin-bottom: 2rem;
  text-align: center;
  padding: 1rem 1.5rem;
  border-radius: 12px;
}

.form-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}

label {
  font-weight: 600;
  margin-bottom: 0.4rem;
  color: #333;
}

input,
textarea {
  background: transparent;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 10px;
  padding: 0.8rem 1rem;
  color: #333;
  font-size: 1rem;
  box-shadow: 0 1px 4px rgba(0, 0, 0, 0.1);
  outline: none;
}

textarea {
  min-height: 120px;
  resize: vertical;
}

button {
  display: block;           /* Permet de gérer les marges correctement */
  width: 100%;   
  margin-top: 2rem;       
  position: relative;
  overflow: hidden;
  background-color: #f7b500;
  color: white;
  font-weight: 600;
  padding: 0.8rem;
  border-radius: 50px;
  border: none;
  cursor: pointer;
  transition: background 0.3s ease;
}

button:hover {
  background-color: #d99a00;
  transform: scale(1.03);
  animation: none;
}

.button::before {
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

.button:hover::before {
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

.wave-transition {
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
  height: 60px;
  margin: 0;
}


.wave-animated {
  transition: d 1s ease-in-out;
}

</style>

