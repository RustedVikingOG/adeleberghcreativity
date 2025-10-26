<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="nav-container">
      <div class="nav-brand">
        <img src="/icon.svg" alt="ABC" class="nav-logo" />
        <span class="nav-title">Adele Bergh</span>
      </div>
      <ul class="nav-menu">
        <li><a @click.prevent="scrollToSection('hero')" href="#hero">Home</a></li>
        <li><a @click.prevent="scrollToSection('about')" href="#about">About</a></li>
        <li><a @click.prevent="scrollToSection('paintings')" href="#paintings">Paintings</a></li>
        <li><a @click.prevent="scrollToSection('photos')" href="#photos">Photos</a></li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  transition: all 0.3s ease;
  background: transparent;
}

.navbar.scrolled {
  background: rgba(255, 255, 255, 0.95);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(10px);
}

.nav-container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-brand {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.nav-logo {
  width: 40px;
  height: 40px;
}

.nav-title {
  font-size: 1.25rem;
  font-weight: 600;
  color: white;
}

.navbar.scrolled .nav-title {
  color: #333;
}

.nav-menu {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-menu a {
  color: white;
  text-decoration: none;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.3s ease;
  padding: 0.5rem 1rem;
  border-radius: 4px;
}

.navbar.scrolled .nav-menu a {
  color: #333;
}

.nav-menu a:hover {
  background: rgba(255, 255, 255, 0.2);
}

.navbar.scrolled .nav-menu a:hover {
  background: rgba(102, 126, 234, 0.1);
  color: #667eea;
}

@media (max-width: 768px) {
  .nav-container {
    padding: 1rem;
  }

  .nav-menu {
    gap: 1rem;
  }

  .nav-menu a {
    padding: 0.25rem 0.5rem;
    font-size: 0.9rem;
  }

  .nav-title {
    font-size: 1rem;
  }

  .nav-logo {
    width: 32px;
    height: 32px;
  }
}
</style>
