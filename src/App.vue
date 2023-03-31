<!-- eslint-disable global-require -->

<script setup lang="ts">
import { Carousel, CarouselSlide } from '@/components';

const slides = [
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
  <carousel
    auto-play
    :timeout="3000"
    #default="{ currentSlideIndex }"
  >
    <carousel-slide
      v-for="(slide, slideIndex) of slides"
      :key="slide.name"
    >
      <div
        class="slide"
        v-show="slideIndex === currentSlideIndex"
      >
        <img
          class="slide__image"
          :src="slide.src"
          alt=""
        />
      </div>
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

.slide {
  width: 100%;
  height: 100%;
}

.slide__image {
  width: 100%;
  max-height: 100%;
  object-fit: cover;
}
</style>
