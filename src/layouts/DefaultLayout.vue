<script setup>
import FooterLayout from '@/components/layout/FooterLayout.vue';
import HeaderLayout from '@/components/layout/HeaderLayout.vue';

</script>



<template>
  <div>
    <HeaderLayout />
    <main>
      <slot />
    </main>
    <FooterLayout/>
  </div>
</template>
