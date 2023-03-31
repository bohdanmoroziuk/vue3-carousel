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

.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.5s ease-in-out;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
}

.slide-enter-to,
.slide-leave-from {
  opacity: 1;
}
</style>
