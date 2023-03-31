<script setup lang="ts">
import {
  ref,
  withDefaults,
  defineProps,
  toRefs,
  onMounted,
  onUnmounted,
} from 'vue';

interface Props {
  autoPlay?: boolean;
  timeout?: number;
}

const props = withDefaults(defineProps<Props>(), {
  autoPlay: false,
  timeout: 1000,
});

const { autoPlay, timeout } = toRefs(props);

type Timer = ReturnType<typeof setInterval>;

const currentSlideIndex = ref(0);

const numberOfSlides = ref(3);

const timer = ref<Timer>();

const showNextSlide = () => {
  if (currentSlideIndex.value === numberOfSlides.value - 1) {
    currentSlideIndex.value = 0;
  } else {
    currentSlideIndex.value += 1;
  }
};

const showPrevSlide = () => {
  if (currentSlideIndex.value === 0) {
    currentSlideIndex.value = numberOfSlides.value - 1;
  } else {
    currentSlideIndex.value -= 1;
  }
};

const checkIsActive = (slideIndex: number) => (
  currentSlideIndex.value === slideIndex
);

const showSlide = (slideIndex: number) => {
  currentSlideIndex.value = slideIndex;
};

const enableAutoPlay = () => {
  if (autoPlay.value) {
    setInterval(showNextSlide, timeout.value);
  }
};

const disableAutoPlay = () => {
  if (timer.value) {
    clearInterval(timer.value);
    timer.value = undefined;
  }
};

onMounted(enableAutoPlay);

onUnmounted(disableAutoPlay);
</script>

<template>
  <div class="carousel">
    <slot :current-slide-index="currentSlideIndex" />

    <div class="carousel__navigation">
      <button
        class="carousel__toggle carousel__toggle--backward"
        @click="showPrevSlide"
      >
        <i class="fas fa-chevron-left"></i>
      </button>
      <button
        class="carousel__toggle carousel__toggle--forward"
        @click="showNextSlide"
      >
        <i class="fas fa-chevron-right"></i>
      </button>
    </div>

    <div class="carousel__pagination">
      <button
        class="carousel__point"
        :class="{ 'carousel__point--active': checkIsActive(slideIndex) }"
        v-for="(_, slideIndex) of numberOfSlides"
        :key="slideIndex"
        @click="showSlide(slideIndex)"
      />
    </div>
  </div>
</template>

<style scoped lang="scss">
.carousel {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

.carousel__navigation {
  position: absolute;
  top: 50%;
  left: 0;
  width: 100%;
  transform: translateY(-50%);
  padding: 0 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.carousel__toggle {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: none;
  background-color: white;
  color: black;
  cursor: pointer;
  font-size: 16px;
  transition: all 0.25s linear;
}

.carousel__toggle:hover {
  background-color: black;
  color: white;
}

.carousel__pagination {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  padding-bottom: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  column-gap: 8px;
}

.carousel__point {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background-color: white;
  border: none;
  cursor: pointer;
}

.carousel__point--active {
  background-color: black;
}
</style>
