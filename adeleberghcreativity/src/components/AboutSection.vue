<script setup lang="ts">
</script>

<template>
  <section id="about" class="about-section">
    <div class="about-container">
      <h2 class="section-title">About Me</h2>
      <div class="about-content">
        <div class="about-text">
          <p>
            Welcome to my creative space! I'm Adele Bergh, an artist and photographer passionate
            about capturing beauty through various mediums.
          </p>
          <p>
            My work explores the intersection of traditional painting techniques and modern
            photography, creating unique visual experiences that tell stories and evoke emotions.
          </p>
          <p>
            Through my art, I aim to inspire others to see the world from different perspectives
            and appreciate the intricate details that often go unnoticed in our daily lives.
          </p>
        </div>
        <div class="about-image-placeholder">
          <div class="placeholder-content">
            <span>Profile Image</span>
            <small>Coming Soon</small>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  min-height: 100vh;
  padding: 6rem 2rem;
  background: linear-gradient(to bottom, #f8f9fa, #ffffff);
}

.about-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 3rem;
  color: #333;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
}

.about-text {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.about-text p {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #555;
}

.about-image-placeholder {
  background: linear-gradient(135deg, #e0c3fc 0%, #8ec5fc 100%);
  border-radius: 12px;
  aspect-ratio: 3/4;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.placeholder-content {
  text-align: center;
  color: white;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.placeholder-content span {
  font-size: 1.5rem;
  font-weight: 600;
}

.placeholder-content small {
  font-size: 1rem;
  opacity: 0.9;
}

@media (max-width: 768px) {
  .about-section {
    padding: 4rem 1rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .about-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .about-text p {
    font-size: 1rem;
  }
}
</style>
