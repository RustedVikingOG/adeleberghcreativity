<template>
  <div class="carousal-div">
    <q-carousel
      swipeable
      animated
      v-model="slide"
      :autoplay="autoplay"
      ref="carousel"
      infinite
      v-model:fullscreen="fullscreen"
    >
      <q-carousel-slide
        v-for="(image, index) in images"
        :key="index"
        :name="index + 1"
        :img-src="image"
      />

      <template v-slot:control>
        <q-carousel-control
          position="top-right"
          :offset="[18, 18]"
          class="text-white rounded-borders"
          style="background: rgba(0, 0, 0, .3); padding: 4px 8px;"
        >
          <q-toggle dense dark color="dark" v-model="autoplay" label="Auto Play" />

          <q-btn
            push dense color="dark" text-color="white"
            :icon="fullscreen ? 'fullscreen_exit' : 'fullscreen'"
            @click="fullscreen = !fullscreen"
            style="margin-left: 16px;"
          />
        </q-carousel-control>

        <q-carousel-control
          position="bottom-right"
          :offset="[18, 18]"
          class="q-gutter-xs"
        >
          <q-btn
            push round dense color="dark" text-color="white" icon="arrow_left"
            @click="$refs.carousel.previous()"
          />
          <q-btn
            push round dense color="dark" text-color="white" icon="arrow_right"
            @click="$refs.carousel.next()"
          />
        </q-carousel-control>
      </template>
    </q-carousel>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  props: {
    images: {
      type: Array,
      default: () => [] // Provide a default empty array
    }
  },
  setup () {
    const slide = ref(1)
    const autoplay = ref(true)

    return {
      slide,
      autoplay,
      fullscreen: ref(false)
    }
  }
}
</script>

<style scoped lang="scss">
.carousal-div {
  border-radius: 12px;
  overflow: hidden;
}
</style>
