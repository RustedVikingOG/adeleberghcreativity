<script setup lang="ts">
</script>

<template>
  <section id="hero" class="hero-banner">
    <div class="hero-content">
      <div class="logo-container">
        <img src="/logo.svg" alt="Adele Bergh Creativity Logo" class="hero-logo" />
      </div>
      <h1 class="hero-title">Adele Bergh Creativity</h1>
      <p class="hero-subtitle">Artist & Photographer</p>
    </div>
  </section>
</template>

<style scoped>
.hero-banner {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  text-align: center;
}

.hero-content {
  padding: 2rem;
}

.logo-container {
  margin-bottom: 2rem;
}

.hero-logo {
  width: 200px;
  height: auto;
  max-width: 100%;
  filter: drop-shadow(0 4px 6px rgba(0, 0, 0, 0.1));
}

.hero-title {
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 1rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
}

.hero-subtitle {
  font-size: 1.5rem;
  font-weight: 300;
  opacity: 0.95;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1.2rem;
  }

  .hero-logo {
    width: 150px;
  }
}
</style>
