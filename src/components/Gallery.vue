<template>
    <div class="p-6 container">
        <h2 class="text-2xl font-bold mb-4 text-center">Image Gallery</h2>

        <!-- Image Grid -->
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
            <img v-for="(img, index) in images" :key="index" :src="img" alt="Gallery"
                class="rounded-sm shadow-md hover:scale-105 transition cursor-pointer" @click="openLightbox(index)" />
        </div>

        <!-- FsLightbox -->
        <FsLightbox :toggler="lightboxToggler" :sources="images" :slide="currentSlide" />
    </div>
</template>

<script setup>
import { ref } from 'vue'
import FsLightbox from 'fslightbox-vue'

// ✅ Local images using Vite-compatible import
const images = [
    new URL('@/assets/images/img1.png', import.meta.url).href,
    new URL('@/assets/images/img2.jpg', import.meta.url).href,
    new URL('@/assets/images/img3.png', import.meta.url).href,

]

const lightboxToggler = ref(false)
const currentSlide = ref(1)

function openLightbox(index) {
    currentSlide.value = index + 1
    lightboxToggler.value = !lightboxToggler.value
}
</script>

<style scoped>
/* Optional: Add styles for smooth image hover */
img {
    width: 100%;
    height: auto;
}

img {
    transition: transform 0.3s ease;
}
</style>
