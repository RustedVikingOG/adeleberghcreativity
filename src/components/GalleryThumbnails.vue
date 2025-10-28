<template>
    <div class="gallery">
      <div
        v-for="(image, index) in images"
        :key="index"
        class="thumbnail-container"
        @click="openZoom(image)"
      >
        <img :src="image" alt="Image" class="thumbnail" />
      </div>
    </div>

    <!-- Image Zoom Modal -->
    <q-dialog v-model="showZoom">
      <q-card class="zoom-modal">
        <q-card-section class="zoom-image-container">
          <img :src="selectedImage" alt="Zoomed Image" class="zoomed-image" />
          <q-btn flat round icon="close" color="white" v-close-popup class="overlay-button" />
        </q-card-section>
      </q-card>
    </q-dialog>
</template>

<script>
export default {
  name: 'GalleryThumbnails',
  props: {
    images: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      showZoom: false,
      selectedImage: null
    }
  },
  methods: {
    openZoom(image) {
      this.selectedImage = image;
      this.showZoom = true;
    }
  }
};
</script>

<style scoped>
.gallery {
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  overflow: hidden;
  flex-wrap: wrap;
  gap: 12px;
  margin: 24px;
  padding-bottom: 24px;
  max-height: 1200px;
  overflow: auto;
}

.thumbnail-container {
  cursor: pointer;
  transition: transform 0.2s;
  width: auto;
  object-fit: contain;
}

.thumbnail-container:hover {
  transform: scale(1.05);
}

.thumbnail {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 8px;
}

.zoom-modal {
  max-width: 90vw;
  max-height: 90vh;
  border-radius: 32px;
}

.zoom-image-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0;
}

.zoomed-image {
  max-width: 100%;
  max-height: 80vh;
  object-fit: contain;
}

.overlay-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: rgba(0, 0, 0, 0.5);
  z-index: 1;
}

@media (max-width: 756px) {
  .gallery {
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
    overflow: hidden;
    flex-wrap: wrap;
    gap: 4px;
    margin: 4px;
    padding-bottom: 24px;
    max-height: 300px;
    overflow: auto;
  }

  .thumbnail {
    height: 70px !important;
  }


}
</style>
