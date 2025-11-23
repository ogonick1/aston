<template>
  <h4 class="container license-title">DIFC license categories</h4>
  <div class="container license-slider">
    <div class="license-slider__sidebar mobile-hidden">
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

        <div class="license-slider__underline"></div>
      </div>
    </div>

    <div
      class="license-slider__content mobile-hidden"
      :class="{ hovered: isHovered }"
      @mouseenter="pauseAutoplay"
      @mouseleave="resumeAutoplay"
    >
      <Transition name="fade" mode="out-in">
        <div v-if="currentSlide" :key="currentSlide.id" class="license-card">
          <div class="license-card__media">
            <SlideMediaCollage
              v-if="currentSlide.id % 2 !== 0"
              :image1="currentSlide.image1"
              :image2="currentSlide.image2"
              :iconSrc="currentSlide.iconSrc"
              :iconSrc2="currentSlide?.iconSrc2"
              :cardDescription="currentSlide.cardDescription"
              :cardLabel="currentSlide.cardLabel"
              :cardDescription2="currentSlide.cardDescription2"
              :slide="currentSlide.id"
            />
            <SlideMediaCollage2
              v-else
              :image1="currentSlide.image1"
              :image2="currentSlide.image2"
              :iconSrc="currentSlide.iconSrc"
              :iconSrc2="currentSlide?.iconSrc2"
              :cardDescription="currentSlide.cardDescription"
              :cardLabel="currentSlide.cardLabel"
              :cardDescription2="currentSlide.cardDescription2"
              :slide="currentSlide.id"
            />
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
              <div class="mobile-hidden">
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
            <div class="desktop-hidden">
              <UIButton
                @mouseenter="isHovered = true"
                @mouseleave="isHovered = false"
                label="Learn more"
              />
            </div>
          </div>
        </div>
      </Transition>
    </div>

        <div
      class="license-slider__content desktop-hidden"
    >
        <div v-for="currentSlide in slides" :key="currentSlide.id" class="license-card">
          <div class="license-card__media">
            <SlideMediaCollage
              v-if="currentSlide.id % 2 !== 0"
              :image1="currentSlide.image1"
              :image2="currentSlide.image2"
              :iconSrc="currentSlide.iconSrc"
              :iconSrc2="currentSlide?.iconSrc2"
              :cardDescription="currentSlide.cardDescription"
              :cardLabel="currentSlide.cardLabel"
              :cardDescription2="currentSlide.cardDescription2"
              :slide="currentSlide.id"
            />
            <SlideMediaCollage2
              v-else
              :image1="currentSlide.image1"
              :image2="currentSlide.image2"
              :iconSrc="currentSlide.iconSrc"
              :iconSrc2="currentSlide?.iconSrc2"
              :cardDescription="currentSlide.cardDescription"
              :cardLabel="currentSlide.cardLabel"
              :cardDescription2="currentSlide.cardDescription2"
              :slide="currentSlide.id"
            />
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
              <div class="mobile-hidden">
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
            <div class="desktop-hidden">
              <UIButton
                label="Learn more"
              />
            </div>
          </div>
        </div>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted, ref, onBeforeUnmount, watch } from 'vue'
import SlideMediaCollage from '../ui/SlideMediaCollage.vue'
import UIButton from '../ui/UIButton.vue'
import SlideMediaCollage2 from '../ui/SlideMediaCollage2.vue'

import slide117 from '@/assets/icons/slide_117.jpg'
import slide118 from '@/assets/icons/slide_118.jpg'
import slide119 from '@/assets/icons/slide-119.jpg'
import slide120 from '@/assets/icons/slide-120.jpg'
import slide121 from '@/assets/icons/slide-121.jpg'
import slide122 from '@/assets/icons/slide-122.jpg'
import slide124 from '@/assets/icons/slide-124.jpg'
import slide123 from '@/assets/icons/slide-123.jpg'
import slide125 from '@/assets/icons/slide-125.jpg'
import slide126 from '@/assets/icons/slide-126.jpg'
import slide127 from '@/assets/icons/slide-127.jpg'
import slide128 from '@/assets/icons/slide-128.jpg'
import slide129 from '@/assets/icons/slide-129.jpg'
import slide130 from '@/assets/icons/slide-130.jpg'

// ICONS
import iconTax from '@/assets/icons/tax.png'
import iconExchange from '@/assets/icons/exchange.png'
import iconUp from '@/assets/icons/up.png'
import iconDiscount from '@/assets/icons/discount.png'
import iconManager from '@/assets/icons/Manager.png'
import iconBank from '@/assets/icons/Bank.png'
import iconInvest from '@/assets/icons/invest-money.png'

const props = defineProps({
  modelValue: {
    type: Number,
    default: 0,
  },
})

const emit = defineEmits(['update:modelValue'])

const slides = [
  {
    id: 1,
    label: 'CATEGORY 1 LICENSE',
    title: 'Full banking',
    description:
      'Licensed to operate as a fully regulated bank in DIFC with deposit-taking, lending, and credit facilities under DFSA oversight.',
    image1: slide117,
    image2: slide118,
    iconSrc: iconTax,
    cardDescription: 'Banking services in DIFC',
    cardLabel: '$10M+',
    cardDescription2: 'Paid-up capital',
  },
  {
    id: 2,
    label: 'CATEGORY 2 LICENSE',
    title: 'Trading & asset management',
    description:
      'Deliver professional investment management and trading operations in DIFC, serving institutional and high-net-worth clients without taking custody of client assets.',
    image1: slide119,
    image2: slide120,
    iconSrc: iconExchange,
    iconSrc2: iconUp,
    cardDescription: 'Proprietary trading desks',
    cardLabel: '',
    cardDescription2: 'Hedge funds',
  },
  {
    id: 3,
    label: 'CATEGORY 3A LICENSE',
    title: 'Investment advisory',
    description:
      'Licensed to arrange and advise on investments in DIFC without custody of client funds, under DFSA oversight.',
    image1: slide121,
    image2: slide122,
    iconSrc: iconDiscount,
    cardDescription: 'Financial arrangers',
    cardLabel: '$250k+',
    cardDescription2: 'Capital',
  },
  {
    id: 4,
    label: 'CATEGORY 3B LICENSE',
    title: 'Principal Trading',
    description:
      'Licensed to trade investments as principal in DIFC using own balance sheet, operating as dealer or market maker under DFSA oversight.',
    image1: slide124,
    image2: slide123,
    iconSrc: iconManager,
    iconSrc2: iconBank,
    cardDescription: 'Deal arranging & advisory',
    cardLabel: '',
    cardDescription2: 'Investment intermediation',
  },
  {
    id: 5,
    label: 'CATEGORY 3C LICENSE',
    title: 'Proprietary trading',
    description:
      'Licensed to conduct proprietary and crypto trading in DIFC using own capital, without holding client funds, under DFSA oversight.',
    image1: slide125,
    image2: slide126,
    iconSrc: iconInvest,
    cardDescription: 'Payment services',
    cardLabel: '$250k+',
    cardDescription2: 'Capital',
  },
  {
    id: 6,
    label: 'CATEGORY 4 LICENSE',
    title: 'Advisory & arranging',
    description:
      'Provide financial advice and arrange investment services without handling client funds',
    image1: slide127,
    image2: slide128,
    iconSrc: iconManager,
    cardDescription: 'Advisory & arranging',
    cardLabel: '$10k-50k',
    cardDescription2: 'Capital',
  },
  {
    id: 7,
    label: 'CATEGORY 5 LICENSE',
    title: 'Fund Management',
    description:
      'Authorized to provide comprehensive financial services in DIFC, offering corporate banking, lending, and capital solutions under full DFSA regulation.',
    image1: slide129,
    image2: slide130,
    iconSrc: iconTax,
    cardDescription: 'Fund management',
    cardLabel: '$500k+',
    cardDescription2: 'Capital',
  },
]


const activeIndex = ref(props.modelValue)

// коли батько міняє v-model → оновлюємо локальний activeIndex
watch(
  () => props.modelValue,
  (val) => {
    if (val !== activeIndex.value) activeIndex.value = val
  },
)

// коли всередині слайдера змінюється activeIndex → віддаємо нагору
watch(activeIndex, (val) => {
  emit('update:modelValue', val)
})

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
  @include header;
  margin-top: 90px;
  margin-bottom: 80px;
  font-size: 52px;
  color: $black;
  line-height: 1.2;
  @media (max-width: 760px) {
    font-size: 36px;
    margin-top: 72px;
    margin-bottom: 24px;
    text-align: center;
  }
}
.license-slider {
  display: grid;
  grid-template-columns: 300px minmax(0, 1fr);
  gap: 40px;
  margin: 0 auto;
  margin-bottom: 90px;
  @media (max-width: 1020px) {
    grid-template-columns: 200px minmax(0, 1fr);
    gap: 20px;
  }
  @media (max-width: 760px) {
    margin-bottom: 50px;
    grid-template-columns: 1fr;
    margin-left: -15px;
    margin-right: -15px;
  }
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
  @media (max-width: 760px) {
  }
}

.license-slider__item-label {
  font-size: 14px;
  line-height: 1.2;
  text-transform: uppercase;
  color: $small-text;
  margin-bottom: 10px;
  @media (max-width: 1020px) {
    font-size: 12px;
  }
  @media (max-width: 760px) {
    font-size: 12px;
  }
}

.license-slider__item-title {
  font-family: 'PTSerif';
  font-size: 20px;
  font-weight: 700;
  line-height: 1.2;
  color: $small-text;
  white-space: nowrap;
  @media (max-width: 1020px) {
    white-space: wrap;
    font-size: 18px;
  }

  @media (max-width: 760px) {
  }
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
  display: flex;
  flex-direction: column;
  gap:40px;
  @media (max-width: 1020px) {
    padding: 16px;
  }
}
.license-slider__content.hovered {
  background: #e3eaf5;
}

/* Картка */
.license-card {
  display: flex;
  flex-direction: column;
  gap: 40px;
  @media (max-width: 1020px) {
    gap: 20px;
  }
}

/* Media блок */
.license-card__media {
  width: 100%;
  height: 342px;
  @media (max-width: 1020px) {
  }
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
  @media (max-width: 1020px) {
    flex-direction: column;
    gap: 0;
  }
}

.license-card__category {
  font-size: 14px;
  letter-spacing: 0.5px;
  text-transform: uppercase;
  color: $small-text;
  margin-bottom: 10px;
}

.license-card__title {
  font-family: 'PTSerif';
  font-size: 36px;
  font-weight: 700;
  line-height: 1.2;
  margin: 0 0 18px;
  color: $black;
  @media (max-width: 1020px) {
    font-size: 28px;
  }
  @media (max-width: 760px) {
    margin: 0;
  }
}

.license-card__description {
  font-size: 18px;
  line-height: 1.5;
  color: $small-text;
  @media (max-width: 1020px) {
    font-size: 16px;
  }
}
.desktop-hidden {
  display: none ;
  button {
    width: 100%;
    max-height: 40px;
  }
  @media (max-width: 760px) {
    display: flex;
  }
}
.mobile-hidden {
  @media (max-width: 760px) {
    display: none;
  }
}
.divider {
  height: 1px;
  background-color: $black;
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


</style>
