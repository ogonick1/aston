<template>
  <div class="media-collage">
    <div v-if="slide === 1" class="media-collage__grid">
      <!-- LEFT big photo -->
      <div class="media-item media-item--image media-item--left">
        <img src="/icons/slider/slide_117.jpg" alt="" />
      </div>
      <!--<div class="star star--middle-right"></div>-->
      <div class="media-star" data-aos="zoom-out">
        <img src="/icons/star-2.png" alt="star" />
        <img class="star-absolute" src="/icons/star-2.png" alt="star" />
      </div>
      <!-- CENTER tall photo -->
      <div class="media-item media-item--image media-item--center">
        <img src="/icons/slider/slide_118.jpg" alt="" />
      </div>

      <!-- RIGHT top card -->
      <div class="media-item media-item--card media-item--brown">
        <div class="media-icon">
          <img src="/icons/tax.png" alt="tax" />
        </div>
        <p class="media-title">Banking services<br />in DIFC</p>
      </div>
      <!--<div class="star star--top-right"></div>-->
      <div class="media-star star-right" data-aos="zoom-out">
        <img src="/icons/star-5.png" alt="star" />
      </div>
      <!-- RIGHT bottom card -->
      <div class="media-item media-item--card media-item--dark-blue">
        <p class="media-title-big">$10M+</p>
        <p class="media-sub">Paid-up capital</p>
      </div>
    </div>
    <div v-else class="slide-img"> <img src="/icons/slider/slide-2.png" alt="slide img"></div>
  </div>
</template>

<script setup>
defineProps({
  slide: {
    type: Number,
    default: 1,
  },
})
</script>

<style scoped lang="scss">
.media-star {
  grid-column: 2 / 3;
  grid-row: 2 / 2;
  display: flex;
  justify-content: center;
  align-items: end;
  position: relative;
}
.star-absolute {
  position: absolute;
  bottom: 0;
  left: 0;
  translate: -100% 100%;
  z-index: 3;
  width: 24px !important;
  height: 24px !important;
}

.star-right {
  grid-column: 4 / 5;
  grid-row: 1 / 2;
  display: flex;
  justify-content: center;
  align-items: start;
}

.media-star img {
  width: 48px;
  height: 48px;
  display: block;
}
.star-right img {
  width: 32px;
  height: 32px;
  display: block;
}

.media-collage {
  width: 100%;
  height: 100%;
  padding: 6px;
  position: relative;
  /*overflow: hidden;*/
}
.slide-img {
  width: 100%;
  height: 100%;
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}

/* GRID 3 columns */
.media-collage__grid {
  /*display: grid;
  grid-template-columns: 1.3fr 1fr 1fr;
  grid-template-rows: 1fr 1fr;
  gap: 8px;
  width: 100%;
  height: 100%;*/
  display: grid;
  grid-template-columns: 1.3fr 8px 1fr 8px 1fr;
  grid-template-rows: 1fr 1fr;
  gap: 8px;
  width: 100%;
  height: 100%;
}

/* === LEFT big image === */
.media-item--left {
  grid-column: 1 / 2;
  grid-row: 1 / span 2;
  border-radius: 8px 8px 64px 8px;
  overflow: hidden;
}

/* === CENTER tall image === */
.media-item--center {
  grid-column: 3 / 4;
  grid-row: 1 / span 2;
  border-radius: 8px 64px 8px 64px;
  overflow: hidden;
}

/* === CARDS (right column) === */
.media-item--card {
  border-radius: 64px 8px 8px 8px;
  padding: 16px;
  padding-bottom: 10px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  color: #fff;
  &:last-child {
    border-radius: 8px 8px 64px 8px;
  }
}

.media-item--brown {
  background: #994d1f;
  grid-column: 5 / 6;
  grid-row: 1 / 2;
}

.media-item--dark-blue {
  background: #353e4e;
  grid-column: 5 / 6;
  grid-row: 2 / 3;
}

.media-icon {
  max-height: 56px;
  display: flex;
  justify-content: center;
}
/* TEXT in cards */
.media-title {
  font-size: 18px;
  line-height: 1.5;
  font-weight: 500;
}

.media-title-big {
  font-size: 36px;
  font-weight: 400;
  margin-bottom: 8px;
}

.media-sub {
  font-size: 18px;
  font-weight: 500;
}

/* IMG */
.media-item--image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* ==== Stars ===== */
/*.star {
  width: 26px;
  height: 26px;
  background-image: url('/icons/star-5.png');
  background-size: contain;
  background-repeat: no-repeat;
  position: absolute;
}
.star-2 {
  width: 26px;
  height: 26px;
  background-image: url('/icons/star-2.png');
  background-size: contain;
  background-repeat: no-repeat;
  position: absolute;
}*/

.star--top-right {
}

.star--middle-right {
}

/* Responsive */
/*@media (max-width: 900px) {
  .media-collage__grid {
    grid-template-columns: 1fr 1fr;
    grid-auto-rows: 180px;
  }
}*/
</style>
