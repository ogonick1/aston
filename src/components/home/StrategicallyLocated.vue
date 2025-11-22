<template>
  <div class="home">
    <div class="container home__wrapper">
      <div class="home__image">
        <img src="/strategically.png" alt="home img" />
      </div>
      <div class="home__right">
        <h3 class="home__right-description-big">
          Strategically located in Dubai’s financial epicenter
        </h3>
        <CheckList :items="check" icon="/icons/check.svg" />
        <div class="home__right-description">
          Whether you are building a private wealth firm, launching a fintech venture, or opening a regulated fund, DIFC provides the framework and support needed to operate legally and competitively.
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import CheckList from '../ui/CheckList.vue';

const check = [
  'Located in central Dubai, next to Emirates Towers and Burj Khalifa',
  'Headquarters for regional and international banks',
  'Home to DIFC FinTech Hive – one of the largest hubs for innovation in the region',
  'Access to NASDAQ Dubai for capital raising and listings',
]
</script>

<style scoped lang="scss">
.home {
  padding-top: 40px;
  padding-bottom: 24px;
  @media (max-width: 760px) {
  }
}
.home__wrapper {
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 40px;
  @media (max-width: 760px) {
    flex-direction: column;
  }
}
.home__right {
  width: 60%;
  max-width: 560px;
  display: flex;
  flex-direction: column;
  gap: 24px;
  @media (max-width: 760px) {
    width: 100%;
  }
  &-description {
    font-size: 20px;
    color: $small-text;
    font-weight: 500;
    @media (max-width: 760px) {
      font-size: 18px;
    }
  }
  &-description-big {
    font-family: PTSerif;
    font-size: 36px;
    color: $black;
    font-weight: 700;
    line-height: 1.3;
    @media (max-width: 760px) {
      font-size: 28px;
    }
  }
}
.home__image {
  width: 460px;
  height: 490px;
  @media (max-width: 1200px) {
    width: 50%;
    height: -webkit-fill-available;
  }
  @media (max-width: 760px) {
    width: 100%;
  }
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
}
</style>
