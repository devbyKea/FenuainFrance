<template>
  <footer class="footer">
    <div class="footer-content">
      <p>🌺 Tous droits réservés — <strong>Fenua in France</strong> © 2025 🌺</p>
    </div>
  </footer>
</template>

<script setup lang="ts">
// Aucun script requis ici
</script>

<style scoped>
.footer {
  margin-top: auto; /* ✅ Fait remonter le footer contre le bas */
  position: relative;
  padding: 1.5rem 1rem;
  text-align: center;
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  color: #3e5f47;
  z-index: 10;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  
  box-shadow: 0 -4px 12px rgba(0, 0, 0, 0.05);
}

.footer-content {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 1rem;
}
</style>
