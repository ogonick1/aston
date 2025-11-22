<template>
  <div class="hero">
    <div class="container hero__wrapper">
      <div class="hero__image">
        <img src="/hero-2.png" alt="hero img" />
      </div>
      <div class="hero__right">
        <div class="hero__right-description">
          The Dubai International Financial Centre (DIFC) is widely regarded as the most prestigious
          financial free zone in the UAE. Known for its independent legal system, international
          regulatory framework, and premium-grade infrastructure, DIFC is home to global banks, law
          firms, wealth managers, and family offices. It is the clear choice for companies seeking a
          regulated presence in the Middle East, with direct access to both regional clients and
          global markets.
        </div>
        <div class="hero__image-mobile">
          <img src="/hero-2.png" alt="hero img" />
        </div>
        <div class="hero__right-divider"></div>
        <div class="hero__right-description-big">
          DIFC operates under its own legal system, based on English common law, and is governed by
          a separate financial regulator, the Dubai Financial Services Authority (DFSA).
        </div>
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style scoped lang="scss">
.hero {
  padding-top: 90px;
  padding-bottom: 90px;
  background-color: $grey;
  @media (max-width: 760px) {
    padding-top: 64px;
    padding-bottom: 64px;
  }
}
.hero__wrapper {
  display: flex;
  justify-content: space-around;
  align-items: center;
  gap: 40px;
  @media (max-width: 760px) {
    flex-direction: column;
  }
}
.hero__right {
  width: 50%;
  max-width: 560px;
  display: flex;
  flex-direction: column;
  gap: 40px;
  @media (max-width: 760px) {
    width: 100%;
  }
  &-description {
    font-size: 18px;
    color: $small-text;
    font-weight: 500;
    @media (max-width: 760px) {
      font-size: 16px;
    }
  }
  &-description-big {
    font-family: 'PTSerif';
    font-size: 24px;
    color: $black;
    font-weight: 700;
    line-height: 1.6;
    @media (max-width: 760px) {
      font-size: 22px;
    }
  }
  &-divider {
    height: 1px;
    width: 100%;
    background-color: $small-text;
  }
}
.hero__image-mobile {
  display: none;
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    aspect-ratio: 1/1;
  }
  @media (max-width: 760px) {
    display: block;
  }
}
.hero__image {
  width: 460px;
  height: 429px;
  @media (max-width: 1200px) {
    width: 50%;
    height: -webkit-fill-available;
  }
  @media (max-width: 760px) {
    display: none;
  }
  //@media (max-width: 760px) {
  //  width: 100%;
  //}
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }
}
</style>
