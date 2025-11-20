<template>
  <ul class="check-list">
    <li v-for="(item, index) in items" :key="index" class="check-list__item" data-aos="zoom-in">
      <img class="check-list__icon" :src="icon" alt="check icon" />

      <span class="check-list__text">
        {{ item }}
      </span>
    </li>
  </ul>
</template>

<script setup>
defineProps({
  items: {
    type: Array,
    required: true,
  },
  icon: {
    type: String,
    required: true,
  },
})
</script>

<style scoped lang="scss">
.check-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.check-list__item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 20px;
  color: $small-text;
  line-height: 1.5;
}

.check-list__icon {
  width: 24px;
  height: 24px;
  flex-shrink: 0;
}

.check-list__text {
  display: block;
  font-size: 20px;
  @media (max-width: 760px) {
    font-size: 18px;
  }
}
</style>
