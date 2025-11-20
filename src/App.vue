<script setup>
import { RouterView } from 'vue-router'
import DefaultLayout from '@/layouts/DefaultLayout.vue'
import AOS from "aos";
import "aos/dist/aos.css";
import { onMounted } from 'vue';

onMounted(() => {
  AOS.init({
    duration: 1000,
    easing: "ease-out",
    delay: 100,
  });
});
</script>

<template>
  <DefaultLayout>
    <RouterView />
  </DefaultLayout>
</template>

<style scoped>
</style>
