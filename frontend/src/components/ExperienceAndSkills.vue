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

        <div class="carousel-container" :style="{ width: carouselWidth + 'px' }" style="margin-top: 50px; margin-bottom: 50px">
          <div class="carousel">
            <div class="carousel-inner" :style="{ transform: 'translateX(' + translateX + 'px)' }">
              <!-- Directly Inserted Images -->
              <div class="carousel-item">
                <img src="@/assets/subito7043.jpg" alt="Carousel Image 1" />
              </div>
              <div class="carousel-item">
                <img src="@/assets/Wind_Tre_Business_logo_2020.svg.png" alt="Carousel Image 2" />
              </div>
              <div class="carousel-item">
                <img src="../assets/codermine_logo.png" alt="Carousel Image 3" />
              </div>
              <div class="carousel-item">
                <img src="@/assets/download.png" alt="Carousel Image 4" style="width: 277px; height: auto;"/>
              </div>
              <div class="carousel-item">
                <img src="@/assets/antares_vision_group_logo.jpeg" alt="Carousel Image 5" style="width: 193px; height: auto;"/>
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

// Define image-related variables
const itemsPerPage = ref(3); // Number of images per page
const itemWidth = ref(250);  // Width of each image
const margin = ref(20);      // Margin between images
const currentIndex = ref(0);
const translateX = ref(0);

// Define a fixed array of images directly (you don't need images from `ref`)
const totalItems = computed(() => 5);  // Since we have 5 images

const carouselWidth = computed(() => {
  return (itemWidth.value + margin.value) * itemsPerPage.value;
});

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

// Auto-slide logic
let autoSlideInterval = null;

onMounted(() => {
  // Start auto-sliding when the component mounts
  autoSlideInterval = setInterval(() => {
    if (currentIndex.value < totalItems.value - itemsPerPage.value) {
      nextSlide();
    } else {
      currentIndex.value = 0;  // Reset to first slide after the last one
      translateX.value = 0;
    }
  }, 1500);
});

onUnmounted(() => {
  // Clear the interval when the component is destroyed
  if (autoSlideInterval) {
    clearInterval(autoSlideInterval);
  }
});

// Skill-related logic
const Skills = ref([
  { id: 1, name: 'BACKEND (JAVA, GO, KOTLIN)', width: '98%' },
  { id: 2, name: 'FRONTEND (HTML, JAVASCRIPT, CSS, VUE, ANGULAR)', width: '88%' },
  { id: 3, name: 'DATABASE MANAGEMENT (SQL, NoSQL, PostgreSQL, MongoDB)', width: '90%' },
  { id: 4, name: 'DEVOPS & CLOUD (DOCKER, KUBERNETES, AWS, CI/CD)', width: '85%' }
]);

const Experiences = ref([
  { id: 1, role: 'Software Engineer', company: 'Microsoft', date: 'Mar 2023 - September 2024' },
  { id: 2, role: 'Frontend Developer', company: 'Spotify', date: 'Mar 2022 - September 2023' }
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
  margin: 2px; /* Add margin around the carousel item */
}

.carousel img {
  width: 250px;
  height: auto;
  object-fit: contain;
}


.carousel-controls {
  display: flex;
  justify-content: center;
}

.carousel-controls button {
  margin: 0 5px;
}
</style>
