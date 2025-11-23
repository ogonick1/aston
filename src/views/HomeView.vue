<script setup>
import { ref } from 'vue'
import BuildBlock from '@/components/home/BuildBlock.vue'
import FeedbackSlider from '@/components/home/FeedbackSlider.vue'
import HomeDescriptions from '@/components/home/HomeDescriptions.vue'
import HomeDiamante from '@/components/home/HomeDiamante.vue'
import HomeHero from '@/components/home/HomeHero.vue'
import HomeSlider from '@/components/home/HomeSlider.vue'
import LegalEntities from '@/components/home/LegalEntities.vue'
import StrategicallyLocated from '@/components/home/StrategicallyLocated.vue'
import TypesCompanies from '@/components/home/TypesCompanies.vue'
import WhyChoose from '@/components/home/WhyChoose.vue'
import BreadCrumbs from '@/components/ui/BreadCrumbs.vue'
import LicensePopupMenu from '@/components/ui/LicensePopupMenu.vue'
import LogosSlider from '@/components/ui/LogosSlider.vue'

const licenseSection = ref(null)

// спільний стан для popup + slider
const activeIndex = ref(0)

const popupItems = [
  { id: 1, badge: '1', title: 'Full banking' },
  { id: 2, badge: '2', title: 'Trading & asset management' },
  { id: 3, badge: '3a', title: 'Investment advisory' },
  { id: 4, badge: '3b', title: 'Principal trading' },
  { id: 5, badge: '3c', title: 'Proprietary trading' },
  { id: 6, badge: '4', title: 'Advisory & arranging' },
  { id: 7, badge: '5', title: 'Fund Management' },
]

function handlePopupSelect(item) {
  const index = popupItems.findIndex((i) => i.id === item.id)
  if (index === -1) return

  activeIndex.value = index

  if (licenseSection.value) {
    licenseSection.value.scrollIntoView({
      behavior: 'smooth',
      block: 'start',
    })
  }
}
</script>

<template>
  <main>
    <BreadCrumbs
      :items="[
        { label: 'Business setup', to: '/' },
        { label: 'DIFC', to: '/difc' },
      ]"
    />
    <HomeHero />
    <HomeDescriptions />
    <LogosSlider />
    <WhyChoose />
    <StrategicallyLocated />
    <HomeDiamante />
    <!--<HomeSlider/>-->
    <section ref="licenseSection">
      <HomeSlider v-model="activeIndex" />
    </section>
      <LicensePopupMenu
    :items="popupItems"
    :active-id="popupItems[activeIndex]?.id"
    @select="handlePopupSelect"
  />
    <TypesCompanies />
    <LegalEntities />
    <BuildBlock />
    <FeedbackSlider />
  </main>
</template>
