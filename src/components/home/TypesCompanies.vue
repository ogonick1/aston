<template>
  <section class="types">
    <div class="container">
      <h4 class="types__title">Types of companies and sectors supported</h4>

      <div class="types__top">
        <p class="types__text">
          DIFC supports a broad range of business activities, with a clear focus on financial,
          legal, and professional services. If your business requires financial licensing, DFSA will
          be the authority responsible for regulating and authorising your firm.
        </p>

        <p class="types__text">
          A dedicated page on our site outlines this process in more detail and explains the
          different licence categories available.
        </p>
      </div>

      <h4 class="types__subtitle">Types of companies include</h4>

      <div class="types__grid">
        <!-- LEFT COLUMN -->
        <div class="types__column">
          <CheckList :size="18" class="check-list" :items="check" icon="/icons/check.svg" />
        </div>

        <!-- RIGHT COLUMN -->
        <div class="types__column">
          <CheckList :size="18" class="check-list" :items="check2" icon="/icons/check.svg" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import CheckList from '../ui/CheckList.vue'

const check = [
  'Full foreign ownership permitted',
  'No restrictions on capital repatriation',
  'Ideal for both startup and multinational setups',
  'Private equity and venture capital firms',
  'Legal, tax, and accounting practices',
]
const check2 = [
  'Fintech platforms and digital payment providers',
  'Insurance, reinsurance, and captive structures',
  'Holding companies and SPVs',
  'International headquarters for multinational groups',
]
</script>

<style scoped lang="scss">

.check-list {
  gap: 19px;
  letter-spacing: 0.005rem;
  letter-spacing: 0.01rem;
}
.types {
  padding: 90px 0;
  background-color: $grey;
  @media (max-width: 760px) {
    padding: 64px 0;
  }

  &__title {
    @include header;
    font-size: 52px;
    font-weight: 700;
    line-height: 1.2;
    margin-bottom: 32px;
    color: $black;
    max-width: 600px;
    @media (max-width: 760px) {
      font-size: 36px;
    }
  }

  &__top {
    display: flex;
    justify-content: space-between;
    gap: 40px;
    margin-bottom: 48px;

    @media (max-width: 760px) {
      flex-direction: column;
      gap: 24px;
    }
  }

  &__text {
    font-size: 20px;
    color: $small-text;
    max-width: 550px;
    letter-spacing: 0.01rem;
    @media (max-width: 760px) {
      font-size: 18px;
    }
  }

  &__subtitle {
    font-family: 'PTSerif';
    font-size: 36px;
    line-height: 1.3;
    font-weight: 700;
    margin-bottom: 24px;
    color: $black;
    @media (max-width: 760px) {
      font-size: 28px;
    }
  }

  &__grid {
    display: flex;
    justify-content: space-between;
    gap: 24px;

    @media (max-width: 760px) {
      flex-direction: column;
    }
  }

  &__column {
    display: flex;
    flex-direction: column;
    gap: 20px;
    max-width: 556px;
  }
}
</style>
