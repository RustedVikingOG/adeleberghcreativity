<script setup lang="ts">
import { ref } from 'vue'

// Placeholder data - will be replaced with Instagram feed later
const photos = ref<Array<{ id: number; title: string }>>([])

// TODO: Connect to Instagram API for photos
// const fetchPhotos = async () => {
//   // Instagram API integration here
// }
</script>

<template>
  <section id="photos" class="gallery-section">
    <div class="gallery-container">
      <h2 class="section-title">Photography</h2>
      <p class="section-subtitle">A collection of captured moments and perspectives</p>

      <div v-if="photos.length === 0" class="empty-state">
        <div class="empty-icon">📷</div>
        <h3>Gallery Coming Soon</h3>
        <p>
          This section will showcase my photography portfolio, connected directly from Instagram.
        </p>
        <p class="empty-hint">Check back soon for updates!</p>
      </div>

      <div v-else class="gallery-grid">
        <!-- Gallery items will be rendered here when connected to Instagram -->
        <div v-for="photo in photos" :key="photo.id" class="gallery-item">
          <div class="gallery-item-content">
            <h4>{{ photo.title }}</h4>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.gallery-section {
  min-height: 100vh;
  padding: 6rem 2rem;
  background: linear-gradient(to bottom, #f8f9fa, #e9ecef);
}

.gallery-container {
  max-width: 1400px;
  margin: 0 auto;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 1rem;
  color: #333;
}

.section-subtitle {
  text-align: center;
  font-size: 1.2rem;
  color: #666;
  margin-bottom: 3rem;
}

.empty-state {
  text-align: center;
  padding: 4rem 2rem;
  max-width: 600px;
  margin: 0 auto;
}

.empty-icon {
  font-size: 4rem;
  margin-bottom: 1.5rem;
}

.empty-state h3 {
  font-size: 2rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 1rem;
}

.empty-state p {
  font-size: 1.1rem;
  color: #666;
  line-height: 1.6;
  margin-bottom: 0.5rem;
}

.empty-hint {
  color: #999 !important;
  font-style: italic;
  margin-top: 1rem;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.gallery-item {
  background: #ffffff;
  border-radius: 12px;
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
}

.gallery-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
}

.gallery-item-content {
  padding: 1.5rem;
}

@media (max-width: 768px) {
  .gallery-section {
    padding: 4rem 1rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .section-subtitle {
    font-size: 1rem;
  }

  .gallery-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}
</style>
