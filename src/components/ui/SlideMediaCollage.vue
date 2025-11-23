<template>
  <div class="media-collage">
    <div  class="media-collage__grid">
      <!-- LEFT big photo -->
      <div class="media-item media-item--image media-item--left">
        <img :src="image1" alt="slide img" />
      </div>
      <!--<div class="star star--middle-right"></div>-->
      <div class="media-star" data-aos="zoom-out">
        <img src="/icons/star-2.png" alt="star" />
        <img class="star-absolute" src="/icons/star-2.png" alt="star" />
      </div>
      <!-- CENTER tall photo -->
      <div class="media-item media-item--image media-item--center">
        <img :src="image2" alt="slide img" />
      </div>

      <!-- RIGHT top card -->
      <div class="media-item media-item--card media-item--brown">
        <div class="media-icon">
          <img :src="iconSrc" alt="tax" />
        </div>
        <p class="media-title">{{cardDescription}}</p>
      </div>
      <!--<div class="star star--top-right"></div>-->
      <div class="media-star star-right" data-aos="zoom-out">
        <img src="/icons/star-5.png" alt="star" />
      </div>
      <!-- RIGHT bottom card -->
      <div class="media-item media-item--card media-item--dark-blue">
        <img v-if="iconSrc2" :src="iconSrc2" width="56" alt="tax" />
        <p v-else class="media-title-big">{{cardLabel}}</p>
        <p class="media-sub">{{cardDescription2}}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  slide: {
    type: Number,
    default: 1,
  },
  image1: {
    type: String,
    default : '/icons/slide_117.jpg'
  },
  image2: {
    type: String,
    default : '/icons/slide_118.jpg'
  },
  iconSrc: {
    type: String,
    default : '/icons/tax.png'
  },
  iconSrc2: {
    type: String,
    required: false,
  },
  cardDescription: {
    type: String,
    default : 'Banking services in DIFC'
  },
  cardLabel: {
    type: String,
    default : '$10M+'
  },
  cardDescription2: {
    type: String,
    default : 'Paid-up capital'
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
  display: grid;
  grid-template-columns: 1.3fr 8px 1fr 8px 1fr;
  grid-template-rows: 1fr 1fr;
  gap: 8px 0;
  width: 100%;
  height: 100%;
  @media (max-width: 760px) {


  }
}

/* === LEFT big image === */
.media-item--left {
  grid-column: 1 / 2;
  grid-row: 1 / span 2;
  border-radius: 8px 8px 64px 8px;
  overflow: hidden;
  @media (max-width: 760px) {
      grid-column: 1 / 2;
  grid-row: 1 / 2;
  }
}

/* === CENTER tall image === */
.media-item--center {
  grid-column: 3 / 4;
  grid-row: 1 / span 2;
  border-radius: 8px 64px 8px 64px;
  overflow: hidden;
    @media (max-width: 760px) {
      grid-column: 1 / 2;
  grid-row: 2 / 2;
  }
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
  font-family: 'PTSerif';
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

@media (max-width: 760px) {
  .media-collage__grid {
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto auto;
    gap: 8px;
  }

  /* Фото 1 (верх-ліво) */
  .media-item--left {
    grid-column: 1 / 2;
    grid-row: 1 / 2;
    border-radius: 32px 4px 32px 4px;
  }

  /* Карта 1 (верх-право) */
  .media-item--brown {
    grid-column: 2 / 3;
    grid-row: 1 / 2;
    border-radius: 4px 32px 4px 32px !important;
    height: 160px;
  }

  /* Карта 2 (низ-ліво) */
  .media-item--dark-blue {
    grid-column: 1 / 2;
    grid-row: 2 / 3;
    border-radius: 4px 32px 4px 32px !important;
    height: 160px;
  }

  /* Фото 2 (низ-право) */
  .media-item--center {
    grid-column: 2 / 3;
    grid-row: 2 / 3;
    border-radius: 32px 4px 32px 4px !important;
    //height: 180px;
  }
}

@media (max-width: 760px) {
  .media-star,
  .star-right {
    position: absolute !important;
    top: 50%;
    left: 50%;
    translate: -50% -50%;
    z-index: 5;
  }

  .media-star img,
  .star-right img {
    width: 36px !important;
    height: 36px !important;
  }

  .star-absolute {
    display: none !important;
  }

  .media-title {
  font-size: 14px;
}

.media-title-big {
  font-family: 'PTSerif';
  font-size: 22px;
}

.media-sub {
  font-size: 18px;
}
}

</style>
