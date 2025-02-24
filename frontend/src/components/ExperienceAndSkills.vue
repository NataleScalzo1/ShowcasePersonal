<template>
  <section class="text-white mt-18" id="skills">
    <div class="absolute right-0 top-[110rem] h-full w-full justify-end">
            <span class="flex opacity-20">
                <span class="w-16 h-32 rounded-l-full flex bg-primary blur-2xl"></span>
                <span class="w-16 h-32 rounded-r-full flex bg-[#f88fc2] blur-2xl mt-14"></span>
            </span>
    </div>
    <div class="md:grid md:grid-cols-2 gap-8 items-center py-8 px-4 xl:gap-16 xl:px-16">
      <div class="mt-4 md:mt-0 text-left flex flex-col z-10 h-full w-[80%]">
        <h2 class="text-4xl font-bold text-white text-left mb-4">My
          <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary">Skills</span>
        </h2>
        <div class="mt-8" v-for="skill in Skills" :key="skill.id">
          <div class="flex items-end justify-between" data-aos="fade-right">
            <h4 class="font-semibold uppercase text-white">
              {{ skill.name }}
            </h4>
            <h3 class="text-2xl font-bold text-white">{{ skill.width }}</h3>
          </div>
          <div class="mt-2 h-1 w-full bg-[#131d30] rounded-full">
            <div class="h-1 rounded-full bg-primary" :style="`width :${skill.width}`"></div>
          </div>
        </div>
      </div>
      <div data-aos="flip-left">
        <h2 class="text-4xl font-bold text-white text-left mb-8 md:text-center md:mt-0 mt-8">My Experiences</h2>

        <div class="carousel-container">
          <div class="carousel">
            <div class="carousel-inner" :style="{ transform: 'translateX(' + translateX + 'px)' }">
              <div class="carousel-item" v-for="(image, index) in images" :key="index">
                <img :src="image.src" :alt="image.alt" />
              </div>
            </div>
          </div>
        </div>
        <p>
          I have had the privilege of working with some of the biggest names in tech. These experiences have allowed me to grow both personally and professionally, learning cutting-edge technologies, working in agile environments, and collaborating with diverse teams. I have gained expertise in various software development practices, and each experience has broadened my understanding of how to build impactful solutions at scale.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue';

const images = ref([
  { src: new URL('@/assets/subito7043.jpg', import.meta.url).href, alt: 'Subito Logo' },
  { src: new URL('@/assets/Wind_Tre_Business_logo_2020.svg.png', import.meta.url).href, alt: 'Wind Tre Logo' },
  { src: new URL('@/assets/codermine_logo.png', import.meta.url).href, alt: 'Codermine Logo' },
  { src: new URL('@/assets/download.png', import.meta.url).href, alt: 'Download Logo' },
  { src: new URL('@/assets/antares_vision_group_logo.jpeg', import.meta.url).href, alt: 'Antares Vision Logo' }
]);

const itemsPerPage = ref(3);
const itemWidth = ref(250);
const margin = ref(20);
const currentIndex = ref(0);
const translateX = ref(0);

const totalItems = computed(() => images.value.length);

function nextSlide() {
  if (currentIndex.value < totalItems.value - itemsPerPage.value) {
    currentIndex.value++;
    translateX.value -= itemWidth.value + margin.value;
  }
}

function prevSlide() {
  if (currentIndex.value > 0) {
    currentIndex.value--;
    translateX.value += itemWidth.value + margin.value;
  }
}

let autoSlideInterval = null;

onMounted(() => {
  autoSlideInterval = setInterval(() => {
    if (currentIndex.value < totalItems.value - itemsPerPage.value) {
      nextSlide();
    } else {
      currentIndex.value = 0;
      translateX.value = 0;
    }
  }, 1500);
});

onUnmounted(() => {
  if (autoSlideInterval) {
    clearInterval(autoSlideInterval);
  }
});

const Skills = ref([
  { id: 1, name: 'BACKEND (JAVA, GO, KOTLIN)', width: '98%' },
  { id: 2, name: 'FRONTEND (HTML, JAVASCRIPT, CSS, VUE, ANGULAR)', width: '88%' },
  { id: 3, name: 'DATABASE MANAGEMENT (SQL, NoSQL, PostgreSQL, MongoDB)', width: '90%' },
  { id: 4, name: 'DEVOPS & CLOUD (DOCKER, KUBERNETES, AWS, CI/CD)', width: '85%' }
]);
</script>

<style scoped>
.carousel-container {
  margin: 0 auto;
  overflow: hidden;
}

.carousel {
  display: flex;
  margin-bottom: 10px;
}

.carousel-inner {
  display: flex;
  transition: transform 1s ease;
}

.carousel-item {
  flex: 0 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  margin: 2px;
}

.carousel img {
  width: 250px;
  height: auto;
  object-fit: contain;
}
</style>
