<script setup>

import { ref } from 'vue';

const imageUrls = [
  'https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  'https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
  'https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=1024&q=60',
];

const app = Vue.createApp({
  setup() {

    const images = ref(imageUrls);
    const activeIndex = ref(0);

    const prevSlide = () => {
      activeIndex.value = (activeIndex.value - 1 + images.value.length) % images.value.length;
    };

    const nextSlide = () => {
      activeIndex.value = (activeIndex.value + 1) % images.value.length;
    };
    return {
      images,
      activeIndex,
      prevSlide,
      nextSlide,
    };
  },
});

</script>

<template>

  <div id="app" class="container mt-5">
    <div class="carousel">
      <div class="carousel-inner">
        <div v-for="(image, index) in imageUrls" :key="index" :class="['carousel-item', index === activeIndex ? 'active' : '']">
          <img :src="image" class="d-block w-100" alt="Slide">
        </div>
      </div>
      <button class="carousel-control-prev" @click="prevSlide">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" @click="nextSlide">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
  
</template>

<style scoped></style>
