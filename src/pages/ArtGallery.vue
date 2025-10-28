<template>
  <div>
    <q-card>
      <GalleryCarousal :images="imagePaths" />
      <q-space />
      <GalleryThumbnails :images="imagePaths" />
      <q-card-section>
        <q-btn flat @click="openInstagram" style="background: url('/logos/instagram.png') no-repeat center center; background-size: contain; width: 100px; height: 25px;"/>
      </q-card-section>
    </q-card>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import GalleryCarousal from 'components/GalleryCarousal.vue';
import GalleryThumbnails from 'components/GalleryThumbnails.vue';
import fileManifest from '../paintings_manifest.json';

const openInstagram = () => {
  window.open('https://www.instagram.com/adelebergh.art/', '_blank');
};

const imagePaths = ref(fileManifest);
</script>
