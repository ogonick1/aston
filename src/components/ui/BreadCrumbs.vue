<template>
  <div class="container">
    <nav class="breadcrumbs">
      <ul class="breadcrumbs__wrapper">
        <li class="breadcrumbs__item" v-for="(item, index) in items" :key="index">
          <RouterLink v-if="item.to && index !== items.length - 1" :to="item.to">
            {{ item.label }}
          </RouterLink>
          <span v-else class="current">
            {{ item.label }}
          </span>
          <span v-if="index !== items.length - 1" class="separator">›</span>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
  items: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped lang="scss">
.breadcrumbs {
  padding: 16px 0;
  background: $white-color;
  &__wrapper {
    display: flex;
    gap: 6px;
    list-style: none;
    padding: 0;
    margin: 0;
    align-items: center;
  }
  &__item {
    display: flex;
    gap: 6px;
  }


  a {
    text-decoration: none;
    color: $small-text;
    transition: 0.5s ease;

    &:hover {
      color: #000;
    }
  }

  .current {
    color: $black;
    font-weight: 600;
  }

  .separator {
    color: #aaa;
  }
}
</style>
