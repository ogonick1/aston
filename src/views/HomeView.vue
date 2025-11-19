<script setup>
import HomeHero from '@/components/home/HomeHero.vue';
import BreadCrumbs from '@/components/ui/BreadCrumbs.vue'
</script>

<template>
  <main>
    <BreadCrumbs
      :items="[
        { label: 'Business setup', to: '/' },
        { label: 'DIFC', to: '/difc' },
      ]"
    />
    <HomeHero/>
  </main>
</template>
