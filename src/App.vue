<!-- eslint-disable global-require -->

<script setup lang="ts">
import { Carousel, CarouselSlide } from '@/components';

const images = [
  {
    name: 'image-1',
    src: require('@/assets/images/image-1.jpg'),
  },
  {
    name: 'image-2',
    src: require('@/assets/images/image-2.jpg'),
  },
  {
    name: 'image-3',
    src: require('@/assets/images/image-3.jpg'),
  },
];
</script>

<template>
  <carousel>
    <carousel-slide
      v-for="image of images"
      :key="image.name"
    >
      <img
        class="image"
        :src="image.src"
        alt=""
      />
    </carousel-slide>
  </carousel>
</template>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.image {
  min-width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
