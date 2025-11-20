<template>
  <h4 class="container license-title">DIFC license categories</h4>
  <div class="container license-slider" @mouseenter="pauseAutoplay" @mouseleave="resumeAutoplay">
    <!-- Ліва колонка з заголовками -->
    <div class="license-slider__sidebar">
      <div
        v-for="(slide, index) in slides"
        :key="slide.id"
        class="license-slider__item"
        :class="{ 'license-slider__item--active': index === activeIndex }"
        @click="setActive(index)"
      >
        <div class="license-slider__item-label">
          {{ slide.label }}
        </div>
        <div class="license-slider__item-title">
          {{ slide.title }}
        </div>

        <!-- активна підкреслена лінія -->
        <div class="license-slider__underline"></div>
      </div>
    </div>

    <!-- Права частина з карткою -->
    <div class="license-slider__content" :class="{ hovered: isHovered }">
      <Transition name="fade" mode="out-in">
        <div v-if="currentSlide" :key="currentSlide.id" class="license-card">
          <div class="license-card__media">
            <SlideMediaCollage :slide="currentSlide.id" />
          </div>

          <div class="license-card__body">
            <div class="license-card__body-top">
              <div>
                <p class="license-card__category">
                  {{ currentSlide.label }}
                </p>
                <h4 class="license-card__title">
                  {{ currentSlide.title }}
                </h4>
              </div>
              <div>
                <UIButton
                  @mouseenter="isHovered = true"
                  @mouseleave="isHovered = false"
                  label="Learn more"
                />
              </div>
            </div>
            <div class="divider"></div>
            <p class="license-card__description">
              {{ currentSlide.description }}
            </p>
          </div>
        </div>
      </Transition>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref, onBeforeUnmount } from 'vue'
import SlideMediaCollage from '../ui/SlideMediaCollage.vue'
import UIButton from '../ui/UIButton.vue'

const slides = [
  {
    id: 1,
    label: 'CATEGORY 1 LICENSE',
    title: 'Full banking',
    description:
      'Licensed to operate as a fully regulated bank in DIFC with deposit-taking, lending, and credit facilities under DFSA oversight.',
  },
  {
    id: 2,
    label: 'CATEGORY 2 LICENSE',
    title: 'Trading & asset management',
    description:
      'Deliver professional investment management and trading operations in DIFC, serving institutional and high-net-worth clients without taking custody of client assets.',
  },
  {
    id: 3,
    label: 'CATEGORY 3A LICENSE',
    title: 'Investment advisory',
    description:
      'Licensed to arrange and advise on investments in DIFC without custody of client funds, under DFSA oversight.',
  },
  {
    id: 4,
    label: 'CATEGORY 3B LICENSE',
    title: 'Principal Trading',
    description:
      'Licensed to trade investments as principal in DIFC using own balance sheet, operating as dealer or market maker under DFSA oversight.',
  },
  {
    id: 5,
    label: 'CATEGORY 3C LICENSE',
    title: 'Proprietary trading',
    description:
      'Licensed to conduct proprietary and crypto trading in DIFC using own capital, without holding client funds, under DFSA oversight.',
  },
  {
    id: 6,
    label: 'CATEGORY 4 LICENSE',
    title: 'Advisory & arranging',
    description:
      'Provide financial advice and arrange investment services without handling client funds',
  },
  {
    id: 7,
    label: 'CATEGORY 5 LICENSE',
    title: 'Fund Management',
    description:
      'Authorized to provide comprehensive financial services in DIFC, offering corporate banking, lending, and capital solutions under full DFSA regulation.',
  },
]

const activeIndex = ref(0)

const currentSlide = computed(() => slides[activeIndex.value])

const AUTOPLAY_DELAY = 5000 // 5s
let autoplayTimer = null

function startAutoplay() {
  stopAutoplay()
  autoplayTimer = window.setInterval(() => {
    activeIndex.value = (activeIndex.value + 1) % slides.length
  }, AUTOPLAY_DELAY)
}

function stopAutoplay() {
  if (autoplayTimer !== null) {
    clearInterval(autoplayTimer)
    autoplayTimer = null
  }
}

function pauseAutoplay() {
  stopAutoplay()
}

function resumeAutoplay() {
  startAutoplay()
}
function setActive(index) {
  activeIndex.value = index
  startAutoplay()
}

onMounted(startAutoplay)
onBeforeUnmount(stopAutoplay)
const isHovered = ref(false)
</script>

<style scoped lang="scss">
.license-title {
  margin-top: 90px;
  margin-bottom: 80px;
  font-size: 52px;
  color: $black;
}
.license-slider {
  display: grid;
  grid-template-columns: 300px minmax(0, 1fr);
  gap: 40px;
  margin: 0 auto;
  margin-bottom: 90px;
}

/* Ліва колонка */
.license-slider__sidebar {
  display: flex;
  flex-direction: column;
}

.license-slider__item {
  padding: 20px 0 20px;
  cursor: pointer;
  position: relative;
  border-bottom: 1px solid $grey;
}

.license-slider__item-label {
  font-size: 14px;
  line-height: 1.2;
  text-transform: uppercase;
  color: $small-text;
  margin-bottom: 10px;
}

.license-slider__item-title {
  font-size: 20px;
  font-weight: 700;
  line-height: 1.2;
  color: $small-text;
  white-space: nowrap;
}

.license-slider__item--active .license-slider__item-title {
  color: $black;
}

.license-slider__underline {
  position: absolute;
  left: 0;
  bottom: 0;
  height: 3px;
  width: 100px;
  background-color: $primary;
  transform: scaleX(0);
  opacity: 0;
  transform-origin: left;
  transition:
    transform 0.5s ease-out,
    opacity 0.3s ease-out;
}

.license-slider__item--active .license-slider__underline {
  transform: scaleX(1);
  opacity: 1;
}

/* Права частина */
.license-slider__content {
  //max-width: 800px;
  background-color: $grey;
  border-radius: 16px;
  padding: 30px;
  transition: all 0.5s ease-out;
}
.license-slider__content.hovered {
  background: #e3eaf5;
}

/* Картка */
.license-card {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

/* Media блок */
.license-card__media {
  width: 100%;
  height: 342px;
}

/* Текстова частина */
.license-card__body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 18px;
}
.license-card__body-top {
  display: flex;
  justify-content: space-between;
  gap: 18px;
}

.license-card__category {
  font-size: 14px;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  color: $small-text;
  margin-bottom: 10px;
}

.license-card__title {
  font-size: 36px;
  font-weight: 700;
  line-height: 1.2;
  margin: 0 0 18px;
  color: $black;
}

.license-card__description {
  font-size: 18px;
  line-height: 1.5;
  color: $small-text;
}

/* Анімація */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Адаптив */
//@media (max-width: 900px) {
//  .license-slider {
//    grid-template-columns: 1fr;
//  }
//  .license-slider__sidebar {
//    order: 1;
//    display: flex;
//    flex-direction: row;
//    overflow-x: auto;
//  }
//  .license-slider__item {
//    margin-right: 20px;
//  }
//  .license-slider__content {
//    order: 2;
//  }
//  .license-card {
//    grid-template-columns: 1fr;
//  }
//}
</style>
