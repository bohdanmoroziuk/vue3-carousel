<script setup lang="ts">
</script>

<template>
  <div class="carousel">
    <slot />
  </div>
</template>

<style scoped lang="scss">
.carousel {
  position: relative;

  min-height: 100vh;
  height: 100vh;
}
</style>
