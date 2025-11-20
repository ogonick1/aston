<script setup>
import HomeDescriptions from '@/components/home/HomeDescriptions.vue';
import HomeDiamante from '@/components/home/HomeDiamante.vue';
import HomeHero from '@/components/home/HomeHero.vue';
import HomeSlider from '@/components/home/HomeSlider.vue';
import StrategicallyLocated from '@/components/home/StrategicallyLocated.vue';
import WhyChoose from '@/components/home/WhyChoose.vue';
import BreadCrumbs from '@/components/ui/BreadCrumbs.vue'
import LogosSlider from '@/components/ui/LogosSlider.vue';
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
    <HomeDescriptions/>
    <LogosSlider/>
    <WhyChoose/>
    <StrategicallyLocated/>
    <HomeDiamante/>
    <HomeSlider/>
  </main>
</template>
