# 🇵🇫 Fenua in France

**Fenua in France** est un site d’information conçu pour aider les jeunes Polynésiens qui arrivent en métropole, notamment à Bordeaux. Il regroupe toutes les démarches essentielles à effectuer en arrivant : sécurité sociale, logement, banque, transports, aides financières, bourses, etc.

Ce projet a pour objectif de faciliter l'intégration en centralisant les ressources utiles dans une interface claire, responsive, et esthétique.

---

## 🎯 Objectif

Arrivé en France en 2018 sans repères, j'ai moi-même dû apprendre toutes ces démarches seul. Ce projet vise à transmettre ces connaissances à d'autres jeunes du fenua, pour leur éviter la galère des débuts.

---

## 🔍 Fonctionnalités principales

- ✅ Liste d’aides essentielles avec titres, catégories, descriptifs, liens utiles et logos
- 🌊 Transitions visuelles animées en forme de vagues (SVG animés)
- 📩 Formulaire de contact fonctionnel (intégrable avec EmailJS)
- 🎨 Design moderne avec effets de *glassmorphism* et responsive
- 📱 Adapté aux mobiles, tablettes et ordinateurs

---

## 🛠️ Stack technique

- **Framework Frontend** : Vue 3 + Vite
- **Langage** : TypeScript
- **Styling** : CSS3 + transitions + animations
- **Email** : EmailJS (préparé pour intégration)
- **Hébergement** : Vercel ou GitHub Pages

---

## 📁 Structure du projet
FenuainFrance/
├── public/ # Images, icônes, logos
├── src/
│ ├── components/ # Composants Vue (Header, Aides, Contact, etc.)
│ ├── views/ # Pages/Sections principales
│ ├── App.vue # Composant racine
│ └── main.ts # Point d'entrée Vue
├── index.html
├── vite.config.ts
└── README.md


---

## 🧑‍💻 Installation en local

### Prérequis

- Node.js (v18 ou plus recommandé)
- npm ou yarn

### Étapes

```bash
git clone https://github.com/devbyKea/FenuainFrance.git
cd FenuainFrance
npm install
npm run dev

Puis ouvre ton navigateur sur :
➡️ http://localhost:5173

✉️ Configuration du formulaire EmailJS
Pour activer l’envoi d’email via le formulaire :

Crée un compte sur https://www.emailjs.com

Configure un service, un template, et récupère ton user ID

Dans le composant Contact.vue, intègre ce code :

ts
Copier
Modifier
import emailjs from 'emailjs-com'

emailjs.send('SERVICE_ID', 'TEMPLATE_ID', {
  from_name: name.value,
  message: message.value,
  reply_to: email.value,
}, 'USER_ID')
⚠️ Les ID sont à obtenir depuis ton tableau de bord EmailJS.
