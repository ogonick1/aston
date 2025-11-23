<template>
  <section class="legal-entities">
    <div class="container legal-entities__inner">
      <!-- LEFT SIDE -->
      <div class="legal-entities__left">
        <p class="legal-entities__eyebrow">LEGAL STRUCTURES</p>

        <h4 class="legal-entities__title">
          Legal entity options<br />
          in DIFC
        </h4>

        <p class="legal-entities__text">
          You may set up your company using one of several legal structures. Each structure has its
          own requirements regarding shareholding, licensing, and reporting.
        </p>

        <p class="legal-entities__text">
          Aston can advise on the best structure based on your business model and any regulatory
          needs.
        </p>
      </div>

      <!-- RIGHT SIDE -->
      <div class="legal-entities__right">
        <UILegalCard
          title="Private Company Limited by Shares (Ltd.)"
          :icon="userIcon"
          variant="light"
        />
        <UILegalCard
          title="Limited Liability Partnership (LLP)"
          :icon="handsIcon"
          variant="peach"
        />
        <UILegalCard title="General Partnership" :icon="globeIcon" variant="peach" />
        <UILegalCard
          title="Special Purpose Company (SPC)"
          :icon="targetIcon"
          variant="light"
        />
        <UILegalCard
          title="Branch of an existing UAE or foreign company"
          :icon="caseIcon"
          variant="light"
          :wide="true"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import UILegalCard from '@/components/ui/UILegalCard.vue'
import userIcon from '@/assets/icons/user.svg'
import handsIcon from '@/assets/icons/hands.svg'
import globeIcon from '@/assets/icons/globe.svg'
import targetIcon from '@/assets/icons/target.svg'
import caseIcon from '@/assets/icons/case.png'
</script>

<style scoped lang="scss">
.legal-entities {
  padding-top: 90px;
  @media (max-width: 760px) {
    padding-top: 64px;
  }

  &__inner {
    display: flex;
    gap: 40px;
    align-items: center;

    @media (max-width: 992px) {
      flex-direction: column;
      gap: 40px;
    }
  }

  &__left {
    max-width: 560px;
  }

  &__eyebrow {
    margin: 0 0 16px;
    font-size: 14px;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    font-weight: 500;
    color: $primary;
    @media (max-width: 760px) {
      font-size: 12px;
    }
  }

  &__title {
    margin: 0 0 24px;
    font-size: 52px;
    line-height: 1.2;
    font-weight: 700;
    color: $black;
    @media (max-width: 760px) {
      font-size: 36px;
    }
  }

  &__text {
    margin: 0 0 14px;
    font-size: 20px;
    color: $small-text;
    @media (max-width: 760px) {
      font-size: 18px;
    }
  }

  &__right {
    flex: 1;
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 16px 20px;

    @media (max-width: 760px) {
      grid-template-columns: 1fr;
    }
  }
}
</style>
