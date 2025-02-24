<template>
  <header class="flex justify-between items-center p-6 bg-gradient-to-r from-gray-600 to-gray-800 relative z-20 shadow-xl rounded-lg">
    <!-- Mobile Toggle Button -->
    <div class="md:hidden z-30">
      <button type="button"
              class="block focus:outline-none"
              @click="isMenuOpen = !isMenuOpen"
      >
                <span v-if="isMenuOpen" class="text-5xl">
                    <img src="https://img.icons8.com/ios-filled/100/ffffff/delete-sign.png" alt="close" width="50" height="50">
                </span>
        <span v-else class="text-5xl">
                    <img src="https://img.icons8.com/ios-filled/100/ffffff/menu--v6.png" alt="menu" width="50" height="50">
                </span>
      </button>
    </div>

    <!-- Navbar Link -->
    <nav
        :class="['fixed inset-0 z-20 flex flex-col items-center justify-center bg-[#111827] md:relative md:bg-transparent md:flex md:justify-between md:flex-row',
            isMenuOpen ? 'block':'hidden'
        ]"
    >
      <ul class="flex flex-col items-center space-y-5 md:flex-row md:space-x-8 md:space-y-0">
        <li v-for="item in Menu" :key="item.name" class="relative group">
          <a :href="item.href"
             class="block text-white text-2xl font-semibold transition duration-300 ease-in-out hover:text-gray-300 md:text-lg p-3 rounded-md transform hover:scale-105 hover:bg-gray-600"
             :class="{ 'text-primary': isActive(item.href) }"
             @click="scrollToSection(item.href)"
          >
            {{ item.name }}
          </a>
          <!-- Add a subtle underline on hover for extra style -->
          <div class="absolute bottom-0 left-0 w-0 h-1 bg-primary transition-all duration-300 ease-in-out group-hover:w-full"></div>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue';
const Menu = ref([
  { name: 'Services', href: '#services' },
  { name: 'About Me', href: '#about' },
  { name: 'Skills', href: '#skills' },
  { name: 'Contact', href: '#contact' },
]);

const isMenuOpen = ref(false);

const scrollToSection = (href) => {
  isMenuOpen.value = false;
  const section = document.querySelector(href);
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' });
  }
};

// Active link state check
const isActive = (href) => {
  return window.location.hash === href;
}
</script>

<style scoped>
/* Custom active link color */
a.text-primary {
  color: #D1D5DB; /* Light grey color for active link */
}

/* Custom hover underline style */
a:hover {
  text-decoration: none;
}

a:hover .group-hover:w-full {
  width: 100%;
}

/* Smooth transition for hover effects */
a {
  transition: all 0.3s ease;
}

.bg-primary {
  background-color: #D1D5DB; /* Light grey for primary color */
}

/* Gradient background for navbar */
.bg-gradient-to-r {
  background-image: linear-gradient(to right, #1b1b47, #1b1b47); /* Grey gradient background */
}

/* Subtle hover background effect for navbar items */
a:hover {
  background-color: #4B5563; /* Darker grey when hovering over items */
}

/* Underline on hover */
.group:hover .group-hover:w-full {
  width: 100%;
}
</style>
