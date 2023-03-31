<script setup lang="ts">
import { ref } from 'vue';

const currentSlideIndex = ref(0);
</script>

<template>
  <div class="carousel">
    <slot :current-slide-index="currentSlideIndex" />
  </div>
</template>

<style scoped lang="scss">
.carousel {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}
</style>
