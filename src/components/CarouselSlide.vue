<script setup lang="ts"></script>

<template>
  <div class="carousel-slide">
    <transition name="slide">
      <div class="carousel-slide__content">
        <slot />
      </div>
    </transition>
  </div>
</template>

<style scoped lang="scss">
.carousel-slide__content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  max-height: 100%;
}
</style>
