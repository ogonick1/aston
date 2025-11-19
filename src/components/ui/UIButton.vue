<template>
  <button class="btn ui-btn">
    <span class="label">
      {{ label }}
    </span>

    <span class="icon"><img src="/icons/ArrowUpRight.svg" height="24" width="24" alt="arrow"></span>
  </button>
</template>

<script setup>
defineProps({
  label: {
    type: String,
    required: true
  }
})
</script>

<style scoped lang="scss">

.ui-btn {
  @include btn-base($secondary, $primary, #dde6f4);
  border: none;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;

  .icon {
    display: inline-block;
    transition: transform 0.5s ease;
  }

  &:hover .icon {
    transform: translateX(10px) rotate(45deg);
  }
}
</style>
