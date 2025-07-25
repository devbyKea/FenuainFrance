<template>
  <section class="aides">
    <h2 class="section-title">
      Aides et Démarches Essentielles
    </h2>

    <div class="card-container">
      <div
        class="card"
        v-for="(aide, index) in aides"
        :key="index"
        @click="toggleDetails(index)"
      >
        <div class="card-content">
          <h3>{{ aide.titre }}</h3>
          <p class="categorie">{{ aide.categorie }}</p>
          <p class="intro">{{ aide.intro }}</p>
          <div v-if="activeCard === index" class="details">
            <p>{{ aide.description }}</p>
<div class="icon-links-wrapper">
  <ul class="icon-links">
    <li v-for="(lien, i) in aide.links" :key="i">
      <a :href="lien.url" target="_blank" rel="noopener">
        <img :src="lien.icon" alt="Logo" class="icon-logo" />
      </a>
    </li>
  </ul>
</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Lien {
  icon: string
  url: string
}

interface Aide {
  titre: string
  intro: string
  description: string
  categorie: string
  links: Lien[]
}

const aides = ref<Aide[]>([
  {
    titre: 'Carte Vitale / Sécurité sociale',
    intro: 'Inscription à la CPAM pour être couvert',
    description: "Si tu viens de Polynésie, tu dois faire ta demande d'ouverture de droits à l'assurance maladie en remplissant le formulaire PUMA. Pour tout remboursement de soins pendant l'ouverture de tes droits, s'adresser à la CPS.",
    categorie: 'Administratif',
    links: [
      { icon: '/icons/pdf.png', url: '/docs/puma.pdf' },
      { icon: '/logos/cpam.png', url: 'https://forum-assures.ameli.fr/questions/1917241-reouverture-droit-cpam-10-ans-polynesie' }
    ]
  },
  {
    titre: 'CAF – Aides au logement / Revenus de solidarité',
    intro: 'Aide financière pour ton logement (APL) / RSA',
    description: "Fais ta demande en ligne sur le site de la CAF. Prépare ton bail, ton RIB, ta pièce d'identité et ton numéro de sécurité sociale.",
    categorie: 'Financier',
    links: [
      { icon: '/logos/caf.png', url: 'https://www.caf.fr' }
    ]
  },
  {
    titre: 'France Travail (ex-Pôle emploi)',
    intro: 'Inscription si tu cherches un emploi',
    description: 'France Travail propose un accompagnement pour les jeunes avec la Mission Locale. Inscription 100% en ligne.',
    categorie: 'Emploi',
    links: [
      { icon: '/logos/ft.png', url: 'https://www.francetravail.fr/accueil/' }
    ]
  },
  {
    titre: 'Compte bancaire avec Boursobank',
    intro: 'Ouvre un compte facilement depuis ton téléphone',
    description: 'Je recommande Boursobank. Rapide, fiable, et tu peux bénéficier de 80 € offerts avec mon lien de parrainage.',
    categorie: 'Banque',
    links: [
      { icon: '/logos/bourso.png', url: 'https://bour.so/p/1XZRmuCI1Bk' }
    ]
  },
  {
    titre: 'Trouver un logement',
    intro: 'Où chercher ? Quels sites utiliser ?',
    description: 'Je recommande Leboncoin et SeLoger. Attention aux arnaques, surtout si c’est trop beau pour être vrai.',
    categorie: 'Logement',
    links: [
      { icon: '/logos/lbc.png', url: 'https://www.leboncoin.fr' },
      { icon: '/logos/seloger.png', url: 'https://www.seloger.com/' }
    ]
  },
  {
    titre: 'Aide au dépôt de garantie',
    intro: 'Avance de caution gratuite',
    description: 'La garantie Visale ou LOCA-PASS permet d’avancer le dépôt de garantie gratuitement.',
    categorie: 'Logement',
    links: [
      { icon: '/logos/visale.png', url: 'https://www.visale.fr' }
    ]
  },
  {
    titre: 'Délégation de la Polynésie à Paris',
    intro: 'Un service qui peut t’accompagner',
    description: 'Le Fare Tama Hau peut t’aider pour des démarches sociales, administratives, et t’orienter.',
    categorie: 'Spécifique Fenua',
    links: [
      { icon: '/logos/pf.png', url: 'https://www.presidence.pf' }
    ]
  },
  {
    titre: 'Bourses CROUS et du Pays',
    intro: 'Aide financière pour les études',
    description: 'Si tu étais déjà boursier via la DFP, tu peux renouveler. Sinon, fais ta demande via messervices.etudiant.gouv.fr.',
    categorie: 'Études',
    links: [
      { icon: '/logos/crous.png', url: 'https://www.messervices.etudiant.gouv.fr' }
    ]
  },
  {
    titre: 'Transports à Bordeaux',
    intro: 'Tram, bus, VCub, tarif solidaire',
    description: 'La TBM propose des abonnements réduits voire gratuits pour les étudiants ou jeunes sans ressources.',
    categorie: 'Vie pratique',
    links: [
      { icon: '/logos/tbm.png', url: 'https://www.infotbm.com/fr' },
      { icon: '/logos/tarif.jpg', url: 'https://www.infotbm.com/fr/tarificationsolidaire' }
    ]
  }
])

const activeCard = ref<number | null>(null)

function toggleDetails(index: number) {
  activeCard.value = activeCard.value === index ? null : index
}
</script>

<style scoped>
.section-title {
  font-family: 'Inter', sans-serif;
  font-size: 2rem;
  font-weight: 700;
  color: #3e5f47; /* même vert foncé que "la ora na" */
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin-bottom: 2rem;
  background: linear-gradient(145deg, #eaf8f0, #ffffff);
  padding: 0.8rem 1.2rem;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.04);
  width: fit-content;
}

.aides {
  background: url('/bg-aides.jpg') no-repeat center top;
  background-size: cover;
  background-attachment: scroll; /* ou 'local' selon ton besoin */
  min-height: 100vh;
  padding: 2rem;
  padding-top: 160px;
  padding-bottom: 10rem;
  font-family: 'Inter', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 0;
  position: relative;
  margin-bottom: 0 !important;
  padding-bottom: 0 !important;
}


.card-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  width: 100%;
}
.card > * {
  position: relative;
  z-index: 3;
}
.card {
  position: relative;
  background: rgba(255, 255, 255, 0.65); /* semi-transparent blanc */
  backdrop-filter: blur(12px) saturate(180%);
  -webkit-backdrop-filter: blur(12px) saturate(180%);
  border-radius: 16px;
  padding: 1.5rem;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
  overflow: hidden;
}


.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 20px rgba(0, 0, 0, 0.08);
}

/* Effet shine */
.card::before {
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
  z-index: 2;
}

.card:hover::before {
  animation: shine 1s ease forwards;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 20px rgba(0, 0, 0, 0.08);
}


@keyframes shine {
  0% {
    left: -75%;
  }
  100% {
    left: 125%;
  }
}




/* Contenu */
.card h3 {
  font-size: 1.4rem;
  color: #3e5f47;
  margin-bottom: 0.5rem;
}

.categorie {
  font-size: 0.85rem;
  font-weight: 600;
  background-color: #fdf0d5;
  color: #d08800;
  display: inline-block;
  padding: 0.2rem 0.5rem;
  border-radius: 4px;
  margin-bottom: 0.6rem;
}

.card .intro {
  color: #4a4a4a;
  margin-bottom: 0.8rem;
}

.details {
  margin-top: 1rem;
  color: #444;
}

.details p {
  margin-bottom: 0.5rem;
  line-height: 1.4;
}

.details ul {
  margin-top: 0.5rem;
  padding-left: 1rem;
}

.details a {
  color: #0a66c2;
  text-decoration: underline;
  font-weight: 500;
  transition: color 0.2s ease;
}

.details a:hover {
  color: #004a99;
}

.icon-links-wrapper {
  display: flex;
  justify-content: center;
  margin-top: 1rem;
}

.icon-links {
  display: flex;
  gap: 0.5rem;
  list-style: none;
  padding: 0;
  margin: 0;
  align-items: center;
}

.icon-links li a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.icon-logo {
  width: 120px;
  height: 120px;
  object-fit: contain;
  filter: grayscale(0.2);
  transition: transform 0.2s ease, filter 0.2s ease;
}

.icon-logo:hover {
  transform: scale(1.1);
  filter: grayscale(0);
}


</style>
