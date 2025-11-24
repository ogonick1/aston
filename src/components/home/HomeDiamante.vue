<template>
  <div class="diamante">
    <div class="container">
      <div class="diamante__wrapper">
        <div class="diamante__image-wrapper">
          <div class="diamante__image">
            <img :src="diamante" alt="icon" />
            <img class="image-star" :src="star" alt="star" />
          </div>
        </div>
        <div class="diamante__descriptions">
          DIFC is designed for those who value compliance, structure, and high-level corporate
          governance. It stands out from other zones by offering a mature legal environment that can
          support long-term business growth across borders.
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import diamante from '@/assets/icons/diamante.svg';
import star from '@/assets/icons/star-1.svg';
</script>

<style lang="scss" scoped>
.diamante {
  display: flex;
  align-items: center;
  padding-top: 40px;
  padding-bottom: 40px;
  position: relative;
  &::before {
    position: absolute;
    content: '';
    width: 100%;
    height: 50%;
    z-index: -1;
    background-color: $grey;
    bottom: 0;
  }
  &__image-wrapper {
    min-width: 100px;
    min-height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  &__image {
    width: 64px;
    height: 56px;
    img {
      width: 100%;
      height: 100%;
      object-fit: contain;
    }
  }
  .image-star {
    position: absolute;
    top: 0;
    right: 0;
    width: 30px;
    height: 30px;
    animation: stars-appear 2.5s ease-out 1s infinite;
  }
}
.diamante__wrapper {
  background-color: $black;
  padding: 60px 40px;
  display: flex;
  align-items: center;
  gap: 40px;
    @media (max-width: 760px) {
    flex-direction: column;
    align-items: start;
    padding: 16px;
    padding-top: 32px;
    gap: 16px;
  }

}
.diamante__image-wrapper {
  position: relative;
}
.diamante__descriptions {
  font-size: 20px;
  font-weight: 500;
  color: $white-color;
  @media (max-width: 760px) {
    font-size: 18px;
  }

}

@keyframes stars-appear {
  0% {
    opacity: 0;
    transform: scale(0.1) translateY(0);
  }
  50% {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
  100% {
    opacity: 0;
    transform: scale(0.1) translateY(0);
  }
}
</style>
