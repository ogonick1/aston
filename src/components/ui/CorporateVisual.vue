<template>
  <!-- VARIANT 1 -->
  <div v-if="variant === 1" class="cv-visual cv-visual--1">
    <!-- LEFT BIG IMAGE -->
    <div class="cv-img">
      <img :src="leftImage" alt="" />
    </div>

    <!-- TOP RIGHT CARD -->
    <div class="cv-card cv-card--dark">
      <div class="cv-card__icon" v-if="cardOneIcon">
        <img :src="cardOneIcon" alt="" />
      </div>
      <div class="cv-card__title">
        {{ cardOneTitle }}
      </div>
      <div class="cv-card__subtitle" v-if="cardOneSubtitle">
        {{ cardOneSubtitle }}
      </div>
    </div>

    <!-- BOTTOM RIGHT CARD -->
    <div class="cv-card cv-card--yellow">
      <div class="cv-card__title cv-card__title--big">
        {{ cardTwoTitle }}
      </div>
      <div class="cv-card__subtitle" v-if="cardTwoSubtitle">
        {{ cardTwoSubtitle }}
      </div>
    </div>
  </div>

  <!-- VARIANT 2 -->
  <div v-else-if="variant === 2" class="cv-visual cv-visual--2">
    <!-- LEFT TOP IMAGE -->
    <div class="cv-img cv-img--small">
      <img :src="leftImage" alt="" />
    </div>

    <!-- RIGHT BIG IMAGE -->
    <div class="cv-img cv-img--big">
      <img :src="rightImage" alt="" />
    </div>

    <!-- LEFT BOTTOM DARK CARD -->
    <div class="cv-card cv-card--dark">
      <div class="cv-card__icon" v-if="cardOneIcon">
        <img :src="cardOneIcon" alt="" />
      </div>
      <div class="cv-card__title">
        {{ cardOneTitle }}
      </div>
      <div class="cv-card__subtitle" v-if="cardOneSubtitle">
        {{ cardOneSubtitle }}
      </div>
    </div>
  </div>

  <!-- VARIANT 3 -->
  <div v-else class="cv-visual cv-visual--3">
    <!-- LEFT BIG IMAGE -->
    <div class="cv-img cv-img--left">
      <img :src="leftImage" alt="" />
    </div>

    <!-- RIGHT TALL IMAGE -->
    <div class="cv-img cv-img--right">
      <img :src="rightImage" alt="" />
    </div>

    <!-- BOTTOM LEFT YELLOW CARD -->
    <div class="cv-card cv-card--yellow cv-card--bottom-left">
      <div class="cv-card__icon" v-if="cardTwoIcon">
        <img :src="cardTwoIcon" alt="" />
      </div>
      <div class="cv-card__title">
        {{ cardTwoTitle }}
      </div>
      <div class="cv-card__subtitle" v-if="cardTwoSubtitle">
        {{ cardTwoSubtitle }}
      </div>
    </div>

    <!-- CENTER DARK CARD -->
    <div class="cv-card cv-card--dark cv-card--center">
      <div class="cv-card__title cv-card__title--big">
        {{ cardOneTitle }}
      </div>
      <div class="cv-card__subtitle" v-if="cardOneSubtitle">
        {{ cardOneSubtitle }}
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  variant: {
    type: Number,
    default: 1,
  },
  leftImage: {
    type: String,
    required: true,
  },
  rightImage: {
    type: String,
    default: '',
  },
  cardOneTitle: {
    type: String,
    default: '',
  },
  cardOneSubtitle: {
    type: String,
    default: '',
  },
  cardOneIcon: {
    type: String,
    default: '',
  },
  cardTwoTitle: {
    type: String,
    default: '',
  },
  cardTwoSubtitle: {
    type: String,
    default: '',
  },
  cardTwoIcon: {
    type: String,
    default: '',
  },
})
</script>

<style scoped lang="scss">
.cv-visual {
  display: grid;
  gap: 8px;
  width: 100%;
  height: 100%;
}

/* ========= VARIANT 1 ========= */
.cv-visual--1 {
  grid-template-columns: 1.6fr 1fr;
  grid-template-rows: repeat(2, 1fr);
  grid-template-areas:
    'img card-top'
    'img card-bottom';
  .cv-img {
    border-radius: 4px 32px 4px 32px;
  }
  .cv-card__icon {
    margin: 0 auto;
  }
    @media (max-width: 760px) {
    grid-template-columns: 1.2fr 1fr;
  }
}

/* ========= VARIANT 2 ========= */
.cv-visual--2 {
  grid-template-columns: 1fr 1.35fr;
  grid-template-rows: 1fr 1fr;
  grid-template-areas:
    'img-small img-big'
    'card-dark img-big';
      .cv-img {
    border-radius: 32px 4px 32px 4px ;
  }
  .cv-img--big {
    border-radius:  4px 32px 4px 32px;
  }
      @media (max-width: 760px) {
    grid-template-columns: 1fr 1fr;
  }
}

/* ========= VARIANT 3 ========= */
.cv-visual--3 {
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr;
  grid-template-areas:
    'img-left img-left img-right'
    'card-yellow card-center img-right';
  @media (max-width: 760px) {
    grid-template-columns: 1fr 1fr;
  }
}

/* IMAGES */
.cv-img {
  border-radius: 4px;
  overflow: hidden;
}

.cv-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* grid areas */
.cv-visual--1 .cv-img {
  grid-area: img;
}

.cv-visual--1 .cv-card--dark {
  grid-area: card-top;
  border-radius: 4px 32px 4px 4px;
}

.cv-visual--1 .cv-card--yellow {
  grid-area: card-bottom;
  border-radius: 4px 4px 32px 4px;
}

.cv-visual--2 .cv-img--small {
  grid-area: img-small;
}

.cv-visual--2 .cv-img--big {
  grid-area: img-big;
}

.cv-visual--2 .cv-card--dark {
  grid-area: card-dark;
  border-radius: 4px 4px 32px 4px;
}

.cv-visual--3 .cv-img--left {
  grid-area: img-left;
  border-radius: 4px 32px 4px  32px;
}

.cv-visual--3 .cv-img--right {
  grid-area: img-right;
  border-radius: 4px 32px 4px  32px;
  @media (max-width: 760px) {
    display: none;
  }
}

.cv-visual--3 .cv-card--bottom-left {
  grid-area: card-yellow;
  border-radius:  32px 4px 4px 4px;
}

.cv-visual--3 .cv-card--center {
  grid-area: card-center;
  border-radius:  4px 4px 32px 4px ;
}

/* CARDS */
.cv-card {
  border-radius: 4px;
  padding: 16px 12px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 8px;
}

.cv-card--dark {
  background-color: #353e4e;
  color: #ffffff;
}

.cv-card--yellow {
  background-color: #ffde76;
  color: $primary;
}

.cv-card__icon img {
  width: 60px;
  height: 60px;
  object-fit: contain;
}

.cv-card__title {
  font-size: 16px;
  font-weight: 500;
  @media (max-width: 760px) {
    font-size: 14px;
  }
}

.cv-card__title--big {
  font-family: 'PTSerif';
  font-size: 36px;
  font-weight: 400;
  line-height: 1.4;
  @media (max-width: 760px) {
    font-size: 28px;
  }
}

.cv-card__subtitle {
  font-size: 16px;
  font-weight: 500;
  line-height: 1.4;
  @media (max-width: 760px) {
    font-size: 14px;
  }
}

/* адаптив (можеш далі підлаштувати під макет) */
//@media (max-width: 900px) {
//  .cv-visual--1,
//  .cv-visual--2,
//  .cv-visual--3 {
//    grid-template-columns: 1fr;
//    grid-template-rows: auto;
//    grid-template-areas: none;
//  }

//  .cv-img,
//  .cv-card {
//    grid-area: auto !important;
//  }
//}
</style>
