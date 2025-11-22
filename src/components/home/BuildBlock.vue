<template>
  <h5 class="title container">Build your presence in DIFC</h5>
  <p class="subtitle container">
    Discover the most effective DIFC structures to establish, manage, and grow your business or
    investment vehicle.
  </p>
  <section class="cv">
    <div class="container cv__inner">
      <div class="cv-tabs">
        <button
          v-for="tab in tabs"
          :key="tab.id"
          class="cv-tab"
          :class="{ 'cv-tab--active': tab.id === activeTabId }"
          type="button"
          @click="setActive(tab.id)"
        >
          <div class="cv-tab__icon" v-if="tab.icon">
            <img :src="tab.icon" :alt="tab.title" />
          </div>

          <div class="cv-tab__content">
            <div class="cv-tab__title">
              {{ tab.title }}
            </div>
            <div class="cv-tab__subtitle">
              {{ tab.subtitle }}
            </div>
          </div>
        </button>
      </div>

      <!-- BOTTOM CONTENT -->
      <Transition name="fade" mode="out-in">
        <div
          class="cv-content"
          v-if="activeTab"
          :key="activeTabId"
          @mouseenter="pause"
          @mouseleave="resume"
        >
          <!-- LEFT COLUMN: LIST -->
          <div class="cv-list">
            <button
              v-for="item in activeTab.items"
              :key="item.id"
              type="button"
              class="cv-list-item"
            >
              <div class="cv-list-item__texts">
                <div class="cv-list-item__title">
                  {{ item.title }}
                </div>
                <div class="cv-list-item__desc">
                  {{ item.description }}
                </div>
              </div>

              <span class="cv-list-item__icon">
                <span class="cv-circle">
                  <!--<img width="16" height="16" src="/icons/ArrowUpRight.svg" alt="arrow">-->
                  <svg
                    width="16"
                    height="16"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M6 18L18 6"
                      stroke="#062150"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                    <path
                      d="M8.25 6H18V15.75"
                      stroke="#062150"
                      stroke-width="2"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                </span>
              </span>
            </button>
          </div>

          <!-- RIGHT COLUMN: CARD -->
          <div class="cv-card">
            <CorporateVisual
              :variant="activeTab.id"
              :left-image="activeTab.leftImage"
              :card-one-icon="activeTab.cardOneIcon"
              :card-one-title="activeTab.cardOneTitle"
              :card-two-title="activeTab?.cardTwoTitle"
              :card-two-subtitle="activeTab.cardTwoSubtitle"
              :right-image="activeTab.rightImage"
              :card-two-icon="activeTab.cardTwoIcon"
              :card-one-subtitle="activeTab?.cardOneSubtitle"
            />
          </div>
        </div>
      </Transition>
    </div>
  </section>
</template>

<script setup>
import { computed, onBeforeUnmount, onMounted, ref } from 'vue'
import CorporateVisual from '../ui/CorporateVisual.vue'

const tabs = [
  {
    id: 1,
    title: 'Structuring',
    subtitle: 'Structures for holding assets, isolating risks, and conducting trading activities.',
    icon: '/icons/legal/build.svg',
    image: '/images/difc-structuring.jpg',
    badge: 'Corporate vehicle options',
    cardTopLabel: 'DIFC',
    cardTitle: 'Holding structure',
    cardBottomLabel: 'Holding structure',
    leftImage: '/icons/build/slide-131.jpg',
    cardOneIcon: '/icons/build/Documents.png',
    cardOneTitle: 'Corporate vehicle options',
    cardTwoTitle: 'DIFC',
    cardTwoSubtitle: 'Holding structure',
    rightImage: '/icons/build/slide-132.jpg',
    cardTwoIcon: '/icons/build/Planning.png',
    items: [
      {
        id: 'holding-company',
        title: 'DIFC holding company setup',
        description: 'A straightforward entity to hold assets and shares in other companies.',
      },
      {
        id: 'spc',
        title: 'DIFC special purpose company (SPC)',
        description: 'A ring-fenced entity designed for specific deals or risk structuring.',
      },
      {
        id: 'proprietary-trading',
        title: 'DIFC proprietary trading company',
        description: 'A company to trade on its own account within DIFC.',
      },
    ],
  },
  {
    id: 2,
    title: 'Finance',
    subtitle:
      'Infrastructure for managing investment funds, financial services, and digital assets.',
    icon: '/icons/legal/hands.svg',
    image: '/images/difc-finance.jpg',
    badge: 'Corporate vehicle options',
    cardTopLabel: 'DIFC',
    cardTitle: 'Financial services',
    cardBottomLabel: 'Fund & asset management',
    leftImage: '/icons/build/slide-133.jpg',
    cardOneIcon: '/icons/build/Diamond.png',
    cardOneTitle: 'Fintech & virtual assets',
    cardTwoTitle: '',
    cardTwoSubtitle: '',
    rightImage: '/icons/build/slide-132.jpg',
    cardTwoIcon: '/icons/build/Planning.png',
    cardOneSubtitle: '',
    items: [
      {
        id: 'fund',
        title: 'DIFC fintech sandbox and innovation testing license (ITL)',
        description: 'Test new fintech products with lighter regulatory requirements.',
      },
      {
        id: 'fin-company',
        title: 'DIFC crypto license',
        description: 'Authorisation to carry out virtual asset activities in DIFC.',
      },
      {
        id: 'fin-tech',
        title: 'DIFC fund registration',
        description: 'Register and manage a fund under the DIFC framework.',
      },
    ],
  },
  {
    id: 3,
    title: 'Wealth',
    subtitle: 'Tools for managing family wealth, succession, and asset protection.',
    icon: '/icons/legal/people.svg',
    image: '/images/difc-wealth.jpg',
    badge: 'Corporate vehicle options',
    cardTopLabel: 'DIFC',
    cardTitle: 'Wealth planning',
    cardBottomLabel: 'Family & private office',
    leftImage: '/icons/build/slide-134.jpg',
    cardOneIcon: '/icons/build/Documents.png',
    cardOneTitle: 'DIFC',
    //cardTwoTitle: '',
    cardTwoSubtitle: 'Wealth planning solutions',
    rightImage: '/icons/build/slide-135.jpg',
    cardTwoIcon: '/icons/build/Planning.png',
    cardOneSubtitle: 'Estate planning',
    items: [
      {
        id: 'foundation',
        title: 'DIFC family office setup',
        description: 'Establish a single- or multi-family office in DIFC.',
      },
      {
        id: 'family-office',
        title: 'DIFC foundations',
        description: 'A flexible structure for asset holding and succession planning.',
      },
      {
        id: 'multi-family-office',
        title: 'DIFC trust structure',
        description:
          'A common law trust for protecting and transferring wealth to the next generation.',
      },
    ],
  },
]

const activeTabId = ref(tabs[0].id)
const activeTab = computed(() => tabs.find((tab) => tab.id === activeTabId.value))

let interval = null
const isPaused = ref(false)

function startAutoplay() {
  if (interval) {
    clearInterval(interval)
  }

  interval = setInterval(() => {
    if (isPaused.value) return

    const currentIndex = tabs.findIndex((t) => t.id === activeTabId.value)
    const nextIndex = (currentIndex + 1) % tabs.length
    activeTabId.value = tabs[nextIndex].id
  }, 5000)
}

function setActive(id) {
  activeTabId.value = id
  startAutoplay()
}

function pause() {
  isPaused.value = true
}

function resume() {
  isPaused.value = false
}

onMounted(() => {
  startAutoplay()
})

onBeforeUnmount(() => {
  if (interval) {
    clearInterval(interval)
  }
})
</script>

<style scoped lang="scss">
.title {
  @include header;
  text-align: center;
  margin-bottom: 24px;
  margin-top: 120px;
  color: $black;
  @media (max-width: 760px) {
    margin-top: 72px;
  }
}
.subtitle {
  font-size: 20px;
  color: $small-text;
  text-align: center;
  @media (max-width: 760px) {
    font-size: 18px;
  }
}
.cv {
  padding-top: 80px;
  padding-bottom: 90px;
  @media (max-width: 760px) {
    padding-top: 48px;
    padding-bottom: 48px;
  }
}

.cv__inner {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

/* TOP TABS */
.cv-tabs {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 16px;
  @media (max-width: 760px) {
    gap: 8px;
  }
}

.cv-tab {
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 24px;
  border-radius: 20px;
  background-color: #ffffff;
  border: 1px solid #d7dae4;
  cursor: pointer;
  text-align: left;
  transition:
    background-color 0.5s ease,
    border-color 0.5s ease,
    box-shadow 0.5s ease;
  @media (min-width: 900px) {
    &:hover {
      background-color: #f5f7fa;
      box-shadow: 0 6px 14px rgba(27, 40, 64, 0.08);
    }
  }
  @media (max-width: 760px) {
    padding: 16px;
  }
}

.cv-tab__icon {
  width: 50px;
  height: 50px;
  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  @media (max-width: 900px) {
    display: none;
  }
}

.cv-tab__title {
  font-family: 'PTSerif';
  font-size: 20px;
  font-weight: 700;
  color: $black;
  margin-bottom: 16px;
  @media (max-width: 900px) {
    margin-bottom: 0px;
    text-align: center;
  }
  @media (max-width: 760px) {
    font-size: 14px;
  }
}

.cv-tab__subtitle {
  font-size: 16px;
  color: $small-text;
  @media (max-width: 900px) {
    display: none;
  }
}

.cv-tab--active {
  background-color: #e3eaf5;
  box-shadow: 0 6px 14px rgba(27, 40, 64, 0.08);
  @media (min-width: 900px) {
    &:hover {
      background-color: #e3eaf5;
    }
  }
}

/* BOTTOM CONTENT */
.cv-content {
  display: grid;
  grid-template-columns: minmax(0, 1.3fr) minmax(0, 1fr);
  gap: 40px;
  padding: 40px;
  background-color: #e3eaf5;
  border-radius: 16px;
  @media (max-width: 760px) {
    gap: 32px;
    min-height: 768px;
  }
}

/* LEFT LIST */
.cv-list {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.cv-list-item {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  cursor: pointer;
  text-align: left;
  border: none;
  border-bottom: 1px solid #d7dae4;
  background-color: transparent;
  transition:
    background-color 0.5s ease,
    box-shadow 0.5s ease,
    transform 0.5s ease;
  padding-bottom: 20px;
  &:last-child {
    padding-bottom: 0;
    border-bottom: none;
  }
  //@media (max-width: 760px) {
  //  &:last-child {
  //    padding-bottom: 0;
  //    border-bottom: none;
  //  }
  //}
}

.cv-list-item__texts {
  max-width: 100%;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.cv-list-item__title {
  font-family: 'PTSerif';
  line-height: 1.2;
  font-size: 20px;
  font-weight: 700;
  color: $black;
  @media (max-width: 760px) {
    font-size: 18px;
  }
}

.cv-list-item__desc {
  font-size: 16px;
  color: $small-text;
  @media (max-width: 760px) {
    font-size: 14px;
  }
}

.cv-list-item__icon {
  flex-shrink: 0;
}

.cv-circle {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border-radius: 99px;
  color: #1b2840;
  background-color: $grey;
  transition: all 0.5s ease;
  svg {
    transition: all 0.5s ease;
  }
}

@media (min-width: 900px) {
  .cv-list-item:hover {
    .cv-circle {
      background: $primary;
      svg > path {
        stroke: #fff;
      }
      svg {
        transform: rotate(45deg);
      }
    }
    .cv-list-item__title {
      color: $primary;
    }
    .cv-list-item__desc {
      color: $black;
    }
  }
}

/* RIGHT CARD */
.cv-card {
  //max-width: 485px;
  max-height: 315px;
  //display: grid;
  //grid-template-rows: auto 1fr;
  //border-radius: 20px;
  //overflow: hidden;
  //background-color: #ffffff;
  //box-shadow: 0 8px 20px rgba(27, 40, 64, 0.08);
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .cv-content {
    grid-template-columns: 1fr;
    padding: 24px;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition:
    opacity 0.4s cubic-bezier(0.22, 0.61, 0.36, 1),
    transform 0.4s cubic-bezier(0.22, 0.61, 0.36, 1);
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
  transform: translateY(0);
}
</style>
