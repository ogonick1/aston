<template>
  <div class="legal-card" :class="[`legal-card--${variant}`, { 'legal-card--wide': wide }]" data-aos="flip-left">
    <div class="legal-card__icon-wrapper" v-if="icon" >
      <img :src="icon" alt="" class="legal-card__icon" />
    </div>

    <div class="legal-card__content">
      <p class="legal-card__title">
        {{ title }}
      </p>
      <p v-if="subtitle" class="legal-card__subtitle">
        {{ subtitle }}
      </p>
    </div>

  </div>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
  subtitle: {
    type: String,
    default: '',
  },
  icon: {
    type: String,
    default: '',
  },
  // variant: "light" | "peach"
  variant: {
    type: String,
    default: 'light',
  },
  // full width
  wide: {
    type: Boolean,
    default: false,
  },
})
</script>

<style scoped lang="scss">
.legal-card {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: space-between;
  gap: 16px;
  padding: 24px;
  border-radius: 20px;
  background-color:#F5F7FA;
  //box-shadow: 0 0 0 1px rgba(10, 10, 10, 0.05);
  min-height: 166px;
  font-family: PTSerif;
  @media (max-width: 760px) {
    min-height: 158px;
  }

  &--peach {
    background-color: #FBF5F1;
  }

  &--light {
    background-color: #f6f8fb;
  }

  &--wide {
    grid-column: 1 / -1;
  }

  &__icon-wrapper {
    width: 50px;
    height: 50px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  &__icon {
    max-width: 100%;
    max-height: 100%;
    display: block;
  }

  &__content {
    display: flex;
    flex-direction: column;
  }

  &__title {
    margin: 0;
    font-size: 20px;
    line-height: 1.35;
    font-weight: 700;
    color: $primary;
  }

  &__subtitle {
    margin: 6px 0 0;
    font-size: 14px;
    line-height: 1.5;
    color: #566173;
  }

}
</style>
