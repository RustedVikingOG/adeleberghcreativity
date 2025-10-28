<template>
  <q-layout view="lHh Lpr lFf" class="main-layout">
    <!-- <div class="background-container">
      <petal-background />
    </div> -->

    <q-card class="header-card subcard-width">
      <div class="logo-container">
        <q-img src="logos/logo.png" fit="contain" />
      </div>
    </q-card>

    <div :style="{ height: isSticky ? `${navbarHeight}px` : '0px' }"></div>
    <q-card ref="navbar" class="navbar subcard-width" :class="{ 'sticky': isSticky }">
      <q-btn-group spread style="height: 36px;">
        <!-- YOU ARE BUSY WITH PHONE VIEW - WORKING ON BUTTON SIZING -->
        <q-btn color="accent" @click="navigateTo('.home-page')">
          <q-icon left name="home" color="warning" />
          <div v-if="dispLabel" class="text-white">Home</div>
        </q-btn>
        <q-btn color="accent" @click="navigateTo('.art-gallery')">
          <q-icon left name="palette" color="info" />
          <div v-if="dispLabel" class="text-white">Art</div>
        </q-btn>
        <q-btn color="accent" @click="navigateTo('.photo-gallery')">
          <q-icon left name="photo_camera" color="positive" />
          <div v-if="dispLabel" class="text-white">Photography</div>
        </q-btn>
        <q-btn color="accent" @click="showModal = true">
          <q-icon left name="phone" color="negative" />
          <div v-if="dispLabel" class="text-white">Contact</div>
        </q-btn>
      </q-btn-group>
    </q-card>

    <q-page-container class="page-width">

      <q-page class="page-spacing over">
        <home-page class="home-page" />
      </q-page>

      <q-page class="page-spacing">
        <art-gallery class="art-gallery" />
      </q-page>

      <q-page class="page-spacing">
        <photo-gallery class="photo-gallery" />
      </q-page>

    </q-page-container>

    <q-dialog v-model="showModal">
      <contact-modal @submit="showModal = false" />
    </q-dialog>
  </q-layout>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import HomePage from 'src/pages/HomePage.vue';
import PhotoGallery from 'src/pages/PhotoGallery.vue';
import ArtGallery from 'src/pages/ArtGallery.vue';
import ContactModal from 'src/components/ContactModal.vue';

defineOptions({
  name: 'MainLayout'
});

const navigateTo = (elementClass: string) => {
  const element = document.querySelector(elementClass);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

const showModal = ref(false);
const navbarHeight = ref(0);
const isSticky = ref(false);
let dispLabel = window.innerWidth <= 756 ? false : true
let stickyThreshold = window.innerWidth <= 756 ? 162 : 262;

const handleResize = () => {
  stickyThreshold = window.innerWidth <= 756 ? 162 : 262;
  dispLabel = window.innerWidth <= 756 ? false : true
};


const handleScroll = () => {
  const navbar = document.querySelector('.navbar');
  if (navbar) {
    navbarHeight.value = (navbar as HTMLElement).offsetHeight;
    const navbarTop = navbar.getBoundingClientRect().top;
    isSticky.value = window.scrollY > stickyThreshold && window.scrollY >= navbarTop;
  }
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
  window.addEventListener('resize', handleResize);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
  window.removeEventListener('resize', handleResize);
});

</script>

<style lang="scss" scoped>
@import '../css/quasar.variables.scss';

.main-layout {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-image: repeating-linear-gradient(to right,
      rgb(98, 98, 98) 0px,
      rgb(98, 98, 98) 50px,
      rgb(90, 89, 89) 50px,
      rgb(90, 89, 89) 100px);
  background-color: #c0c0c0;
}

.header-card {
  margin: 32px auto;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
  overflow: hidden;
}

.logo-container {
  height: 95%;
  width: 95%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.header-content {
  font-family: 'Italianno', sans-serif !important;
}

.navbar {
  height: 36px;
  position: relative;
  z-index: 10;
  transition: position 0.3s;

  .q-btn {
    .q-icon {
      color: red;
    }
  }
}

.navbar.sticky {
  position: fixed;
  top: 0;
  margin-top: 4px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.3);
}

.q-page:first-of-type {
  margin-top: 32px;
}

@media (max-width: 756px) {
  .header-card {
    width: 90%;
    height: 100px;
  }

  .logo-space {
    height: 70%;
    width: 30px;
    margin-right: 16px;
    margin-top: auto;
    margin-bottom: auto;
  }

  .header-content {
    font-family: 'Italianno', sans-serif !important;
    width: 80%;

    h1 {
      line-height: 3.5rem !important;
    }
  }

  .q-btn {
    padding: 0 8px;
    min-height: 32px;

    .q-icon {
      font-size: 16px;
    }

    .q-btn__content {
      line-height: 1;
    }
  }
}
</style>
