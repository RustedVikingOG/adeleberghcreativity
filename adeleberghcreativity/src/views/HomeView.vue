<script setup lang="ts">
import NavBar from '@/components/NavBar.vue'
import HeroBanner from '@/components/HeroBanner.vue'
import AboutSection from '@/components/AboutSection.vue'
import PaintingGallery from '@/components/PaintingGallery.vue'
import PhotosGallery from '@/components/PhotosGallery.vue'
import FooterSection from '@/components/FooterSection.vue'
</script>

<template>
  <div class="home-view">
    <NavBar />
    <HeroBanner />
    <AboutSection />
    <PaintingGallery />
    <PhotosGallery />
    <FooterSection />
  </div>
</template>

<style scoped>
.home-view {
  width: 100%;
  overflow-x: hidden;
}
</style>
