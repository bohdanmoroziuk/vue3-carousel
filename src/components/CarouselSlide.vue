<script setup lang="ts"></script>

<template>
  <div class="carousel-slide">
    <transition name="slide">
      <slot />
    </transition>
  </div>
</template>

<style scoped lang="scss">
.carousel-slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
