<template>
  <section class="text-white mt-20" id="testimonials" data-aos="zoom-in">
    <div data-aos="flip-left">
      <h2 class="text-4xl font-bold text-white text-left mb-8 md:text-center md:mt-0 mt-8">My Skills</h2>

      <div class="carousel-container">
        <div class="carousel">
          <div class="carousel-inner">
            <div class="carousel-item" v-for="(image, index) in images.concat(images)" :key="index">
              <img :src="image" alt="Carousel Image" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const images = ref([
  new URL('@/assets/go_logo-removebg-preview.png', import.meta.url).href,
  new URL('@/assets/vue_logo-removebg-preview.png', import.meta.url).href,
  new URL('@/assets/java_logo-removebg-preview.png', import.meta.url).href,
  new URL('@/assets/spring_logo.png', import.meta.url).href,
  new URL('@/assets/kotlin_logo.png', import.meta.url).href,
  new URL('@/assets/html-js-css.png', import.meta.url).href,
  new URL('@/assets/mysql.png', import.meta.url).href,
  new URL('@/assets/postgres-removebg-preview.png', import.meta.url).href,
  new URL('@/assets/aws.png', import.meta.url).href,
  new URL('@/assets/jenkins-removebg-preview.png', import.meta.url).href,

]);
</script>

<style scoped>
.carousel-container {
  margin: 0 auto;
  overflow: hidden;
  width: 90%;
  position: relative;
}

.carousel {
  display: flex;
  overflow: hidden;
}

.carousel-inner {
  display: flex;
  animation: scrollCarousel 20s linear infinite;
  width: max-content;
}

.carousel-item {
  flex: 0 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 10px;
}

.carousel img {
  width: 250px;
  height: auto;
  object-fit: contain;
}

@keyframes scrollCarousel {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}
</style>
