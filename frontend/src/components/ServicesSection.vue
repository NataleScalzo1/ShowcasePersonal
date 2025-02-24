<template >
    <section class="text-white mt-20" id="services">
        <div class="px-4 xl:pl-16">
            <h2 class="text-4xl font-bold text-white mb-4">My Services</h2>
        </div>
        <div class="py-8 xl:px-16 px-4 sm:py-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3">
            <div v-for="service in services" :key="service.id" data-aos="fade-up"
            class="px-8 py-12 rounded-xl bg-[#111a3e] shadow-lg border border-[#1f1641]"
            >
                <div class="mx-auto h-24 w-24 text-center xl:h-28 xl:w-28">
                    <div>
                        <img :src="service.icon" alt="service icon">
                    </div>
                </div>
                <div class="text-center">
                    <h3 class="pt-8 text-lg font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl">
                        {{ service.name }}
                    </h3>
                    <p class="text-grey pt-4 text-sm group-hover:text-white md:text-base">
                        {{ service.description }}
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>
<script setup>
import {ref} from 'vue';
const services =ref([
    {
        id:1,
        icon:'https://img.icons8.com/ios-filled/100/ffffff/google-code.png',
        name:'WEB DEVELOPMENT',
        description:'I create responsive, high-performance websites and web applications using modern technologies. From frontend design to backend logic, I build scalable and user-friendly solutions tailored to your needs.'
    },
    {
        id:2,
        icon:'https://img.icons8.com/?size=100&id=8305&format=png&color=000000',
        name:'DATABASE MANAGEMENT',
        description:'I design, optimize, and maintain relational and non-relational databases to ensure data integrity, security, and performance. From schema design to query optimization, I create efficient data solutions for scalable applications.'
    },
    {
        id:4,
        icon:'https://img.icons8.com/ios-filled/100/ffffff/email-open.png',
        name:'CLOUD SOLUTIONS',
        description:'I design and implement scalable, secure, and efficient cloud-based architectures. Whether deploying applications, managing infrastructure, or optimizing cloud resources, I ensure high availability and performance.'
    },
    ])
</script>

