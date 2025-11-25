<template>
  <div class="container why">
    <div class="why__left">
      <h2 class="why__left-title">Why choose DIFC?</h2>
      <div class="why__left-description">
        The zone offers a stable and transparent environment that appeals to serious investors,
        financial professionals, and founders who require structure, trust, and international
        credibility.
      </div>
      <CheckList2  class="desktop check-list" :items="benefits" icon="/icons/check.svg" />
    </div>
    <div class="why__image">
      <div class="why__image-main">
        <img src="/why.jpg" alt="why img" />
      </div>
      <div class="why__image-small" data-aos="fade-up">
        <div class="why__image-stars">For high-level corporate governance</div>
        <svg
          class="why__image-graph"
          width="210"
          height="95"
          viewBox="0 0 210 95"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M209.189 0.233398L203.421 9.53227e-05L206.103 5.11266L209.189 0.233398ZM195.493 9.22097L195.953 9.41521L195.493 9.22097ZM187.819 25.2584L187.506 24.8686L187.819 25.2584ZM189.885 22.5207L189.425 22.3265L189.885 22.5207ZM177.013 33.9398L176.7 33.5501L177.013 33.9398ZM166.837 34.7531L167.22 35.0751L166.837 34.7531ZM153.519 38.4446L153.155 38.7872L153.519 38.4446ZM163.973 38.156L163.591 37.834L163.973 38.156ZM142.603 34.6891L142.852 35.1228L142.603 34.6891ZM151.186 35.9644L151.55 35.6219L151.186 35.9644ZM134.435 34.4967L134.097 34.865L134.435 34.4967ZM141.557 35.2897L141.308 34.856L141.557 35.2897ZM120.299 47.4857L120.762 47.6747L120.299 47.4857ZM110.17 55.4235L110.616 55.6511L110.17 55.4235ZM114.837 51.7873L114.725 51.2999L114.837 51.7873ZM99.6724 75.9582L99.2272 75.7306L99.6724 75.9582ZM86.6074 83.2307L86.1761 82.9777L86.6074 83.2307ZM73.7871 86.4382L73.3999 86.7546L73.7871 86.4382ZM85.2465 85.5511L85.6778 85.804L85.2465 85.5511ZM68.8156 82.5452L68.6941 83.0302L68.8156 82.5452ZM72.5365 84.9072L72.1492 85.2235L72.5365 84.9072ZM55.7761 80.4481L55.9388 80.9209L55.7761 80.4481ZM59.7552 80.2764L59.6338 80.7615L59.7552 80.2764ZM45.1986 79.0851L44.7905 79.374L45.1986 79.0851ZM52.7092 81.504L52.872 81.9768L52.7092 81.504ZM31.6795 82.5115L32.0686 82.8254L31.6795 82.5115ZM9.38065 90.4828L9.19174 90.0198L9.38065 90.4828ZM12.2378 88.3294L11.8448 88.0203L12.2378 88.3294ZM0.189453 94.2334L0.378363 94.6963L9.56956 90.9457L9.38065 90.4828L9.19174 90.0198L0.000542849 93.7705L0.189453 94.2334ZM12.2378 88.3294L12.6307 88.6385L15.7502 84.6728L15.3572 84.3637L14.9642 84.0546L11.8448 88.0203L12.2378 88.3294ZM31.6795 82.5115L32.0686 82.8254L35.0988 79.0695L34.7097 78.7555L34.3206 78.4415L31.2903 82.1975L31.6795 82.5115ZM52.7092 81.504L52.872 81.9768L55.9388 80.9209L55.7761 80.4481L55.6133 79.9754L52.5465 81.0313L52.7092 81.504ZM59.7552 80.2764L59.6338 80.7615L68.6941 83.0302L68.8156 82.5452L68.937 82.0602L59.8767 79.7914L59.7552 80.2764ZM72.5365 84.9072L72.1492 85.2235L73.3999 86.7546L73.7871 86.4382L74.1744 86.1219L72.9237 84.5909L72.5365 84.9072ZM85.2465 85.5511L85.6778 85.804L87.0387 83.4836L86.6074 83.2307L86.1761 82.9777L84.8152 85.2981L85.2465 85.5511ZM92.6456 79.7719V80.2719H93.4397V79.7719V79.2719H92.6456V79.7719ZM99.6724 75.9582L100.118 76.1858L110.616 55.6511L110.17 55.4235L109.725 55.1959L99.2272 75.7306L99.6724 75.9582ZM114.837 51.7873L114.949 52.2746L115.497 52.1488L115.385 51.6615L115.273 51.1742L114.725 51.2999L114.837 51.7873ZM120.299 47.4857L120.762 47.6747L125.179 36.8604L124.716 36.6714L124.253 36.4823L119.836 47.2966L120.299 47.4857ZM141.557 35.2897L141.805 35.7234L142.852 35.1228L142.603 34.6891L142.354 34.2555L141.308 34.856L141.557 35.2897ZM151.186 35.9644L150.822 36.307L153.155 38.7872L153.519 38.4446L153.883 38.102L151.55 35.6219L151.186 35.9644ZM163.973 38.156L164.356 38.4779L167.22 35.0751L166.837 34.7531L166.455 34.4312L163.591 37.834L163.973 38.156ZM177.013 33.9398L177.326 34.3296L188.132 25.6481L187.819 25.2584L187.506 24.8686L176.7 33.5501L177.013 33.9398ZM189.885 22.5207L190.346 22.715L195.953 9.41521L195.493 9.22097L195.032 9.02672L189.425 22.3265L189.885 22.5207ZM198.691 5.74173L198.923 6.1845L205.437 2.76684L205.205 2.32408L204.972 1.88132L198.458 5.29897L198.691 5.74173ZM195.493 9.22097L195.953 9.41521C196.539 8.02664 197.588 6.88461 198.923 6.1845L198.691 5.74173L198.458 5.29897C196.919 6.1068 195.707 7.42452 195.032 9.02672L195.493 9.22097ZM187.819 25.2584L188.132 25.6481C189.102 24.8691 189.863 23.8611 190.346 22.715L189.885 22.5207L189.425 22.3265C189.006 23.3198 188.346 24.1934 187.506 24.8686L187.819 25.2584ZM172.202 34.0762L171.911 34.4831C173.547 35.651 175.759 35.5883 177.326 34.3296L177.013 33.9398L176.7 33.5501C175.482 34.5281 173.763 34.5768 172.492 33.6693L172.202 34.0762ZM166.837 34.7531L167.22 35.0751C168.39 33.6847 170.432 33.427 171.911 34.4831L172.202 34.0762L172.492 33.6693C170.589 32.3101 167.961 32.6418 166.455 34.4312L166.837 34.7531ZM153.519 38.4446L153.155 38.7872C156.229 42.0557 161.466 41.9111 164.356 38.4779L163.973 38.156L163.591 37.834C161.087 40.8094 156.548 40.9348 153.883 38.102L153.519 38.4446ZM142.603 34.6891L142.852 35.1228C145.462 33.6249 148.76 34.1148 150.822 36.307L151.186 35.9644L151.55 35.6219C149.171 33.0924 145.366 32.5271 142.354 34.2555L142.603 34.6891ZM134.435 34.4967L134.097 34.865C136.205 36.8004 139.323 37.1477 141.805 35.7234L141.557 35.2897L141.308 34.856C139.204 36.0635 136.56 35.7691 134.773 34.1283L134.435 34.4967ZM124.716 36.6714L125.179 36.8604C126.645 33.2709 131.24 32.2426 134.097 34.865L134.435 34.4967L134.773 34.1283C131.404 31.0348 125.983 32.2479 124.253 36.4823L124.716 36.6714ZM115.385 51.6615L115.497 52.1488C117.875 51.6029 119.839 49.9339 120.762 47.6747L120.299 47.4857L119.836 47.2966C119.037 49.2546 117.334 50.701 115.273 51.1742L115.385 51.6615ZM110.17 55.4235L110.616 55.6511C111.49 53.9405 113.077 52.7044 114.949 52.2746L114.837 51.7873L114.725 51.2999C112.565 51.7958 110.734 53.2221 109.725 55.1959L110.17 55.4235ZM93.4397 79.7719V80.2719C96.2563 80.2719 98.8355 78.6937 100.118 76.1858L99.6724 75.9582L99.2272 75.7306C98.1161 77.9042 95.8808 79.2719 93.4397 79.2719V79.7719ZM86.6074 83.2307L87.0387 83.4836C88.2055 81.4941 90.3391 80.2719 92.6456 80.2719V79.7719V79.2719C89.9843 79.2719 87.5224 80.6821 86.1761 82.9777L86.6074 83.2307ZM73.7871 86.4382L73.3999 86.7546C76.706 90.8019 83.0341 90.3119 85.6778 85.804L85.2465 85.5511L84.8152 85.2981C82.524 89.205 77.0396 89.6296 74.1744 86.1219L73.7871 86.4382ZM68.8156 82.5452L68.6941 83.0302C70.0519 83.3702 71.2637 84.1395 72.1492 85.2235L72.5365 84.9072L72.9237 84.5909C71.902 83.34 70.5037 82.4525 68.937 82.0602L68.8156 82.5452ZM55.7761 80.4481L55.9388 80.9209C57.1291 80.5111 58.4127 80.4557 59.6338 80.7615L59.7552 80.2764L59.8767 79.7914C58.4677 79.4386 56.9866 79.5025 55.6133 79.9754L55.7761 80.4481ZM45.1986 79.0851L44.7905 79.374C46.6073 81.9402 49.8991 83.0004 52.872 81.9768L52.7092 81.504L52.5465 81.0313C49.9935 81.9103 47.1668 80.9998 45.6067 78.7962L45.1986 79.0851ZM34.7097 78.7555L35.0988 79.0695C37.6307 75.9312 42.4607 76.083 44.7905 79.374L45.1986 79.0851L45.6067 78.7962C42.8935 74.9637 37.269 74.787 34.3206 78.4415L34.7097 78.7555ZM23.5407 83.4095L23.2293 83.8008C25.9431 85.9602 29.891 85.5246 32.0686 82.8254L31.6795 82.5115L31.2903 82.1975C29.4579 84.4689 26.1357 84.8355 23.852 83.0183L23.5407 83.4095ZM15.3572 84.3637L15.7502 84.6728C17.5703 82.3589 20.9257 81.9677 23.2293 83.8008L23.5407 83.4095L23.852 83.0183C21.1144 80.84 17.1272 81.3048 14.9642 84.0546L15.3572 84.3637ZM9.38065 90.4828L9.56956 90.9457C10.7726 90.4548 11.8274 89.6598 12.6307 88.6385L12.2378 88.3294L11.8448 88.0203C11.1486 88.9053 10.2344 89.5944 9.19174 90.0198L9.38065 90.4828Z"
            fill="#062150"
          />
        </svg>
      </div>
    </div>
    <CheckList2 class="mobile check-list" :items="benefits" icon="/icons/check.svg"/>
    <button class="btn btn-primary mobile">Contact us</button>
  </div>
</template>

<script setup>
import CheckList2 from '../ui/CheckList2.vue'
const benefits = [
  'Independent jurisdiction with English-language common law',
  '100% foreign ownership and no currency controls',
  'No restrictions on profit repatriation',
  '50-year guarantee of zero tax on income and profits',
  'International arbitration centre and courts with global recognition',
]
</script>

<style scoped lang="scss">
.btn-primary {
  width: 100%;
  @include btn-base($primary, #ffffff, $black);
}
.desktop {
  display: flex;
  @media (max-width: 760px) {
    display: none;
  }
}
.mobile {
  display: none;
  @media (max-width: 760px) {
    display: block;
  }
}

.why {
  padding-top: 70px;
  margin-bottom: 60px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 40px;

  @media (max-width: 760px) {
    flex-direction: column;
    justify-content: start;
    padding-top: 24px;
    margin-bottom: 24px;
  }
}
.why__left {
  width: 65%;
  max-width: 580px;
  display: flex;
  flex-direction: column;
  gap: 24px;
  @media (max-width: 1020px) {
    width: 60%;
  }
  @media (max-width: 760px) {
    width: 100%;
  }
  &-title {
    @include header;
    font-size: 52px;
    color: $black;
    font-weight: 700;
    line-height: 1.2;
    @media (max-width: 1200px) {
      font-size: 36px;
    }
  }
  &-description {
    font-size: 20px;
    color: $small-text;
    font-weight: 500;
    @media (max-width: 760px) {
      font-size: 18px;
    }
  }
}
.why__image {
  width: 40%;
  max-width: 460px;
  position: relative;
  display: flex;
  //@media (max-width: 1200px) {
  //  width: 50%;
  //}
  @media (max-width: 760px) {
    width: 100%;
  }
  &-main {
    width: 316px;
    height: 420px;
    overflow: hidden;
    border-radius: 120px 4px 60px 4px;
    margin-bottom: 80px;
    @media (max-width: 760px) {
      //width: 90%;
      //height: 90%;
    }
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
    }
  }
  &-small {
    position: absolute;
    border-radius: 2px 2px 120px 2px;
    border: 1px solid $grey;
    z-index: 2;
    bottom: 0;
    right: 0;
    width: 258px;
    height: 258px;
    background-color: #E3EAF5;
    padding: 24px;
    color: #062150;
    @media (max-width: 1020px) {
      width: 184px;
      height: 184px;
    }
  }

  &-house {
    width: 70px;
    height: 54px;
    margin: 45px 0px 0px 45px;
    @media (max-width: 760px) {
      width: 40px;
      height: 30px;
      margin: 28px 0px 0px 20px;
    }
  }
  &-stars {
    font-family: 'Inter';
    font-size: 24px;
    line-height: 1.2;
    font-weight: 500;
    letter-spacing: 0.005rem;
    position: absolute;
    left: 18px;
    top: 18px;
    width: 180px;
    height: auto;
    opacity: 0;
    transform: scale(0.4) translateY(-8px);
    animation: stars-appear 2s ease-out 1s forwards;
    @media (max-width: 1020px) {
      left: 8px;
      top: 9px;
      width: 125px;
      font-size: 18px;
    }
  }

  /* SVG-графік */
  .why__image-graph {
    position: absolute;
    left: 15px;
    bottom: 25px;
    width: 206px;
    height: auto;

    opacity: 0;
    transform: translateY(8px);

    animation: graph-fade-in 1s ease-out 1s forwards;
    @media (max-width: 1200px) {
      width: 190px;
    }
    @media (max-width: 1020px) {
      width: 125px;
    }
  }
}
/* Анімація зірочок */
@keyframes stars-appear {
  0% {
    opacity: 0;
    transform: scale(0.4) translateY(-8px);
  }
  60% {
    opacity: 1;
    transform: scale(1.05) translateY(0);
  }
  100% {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}

@keyframes graph-fade-in {
  from {
    opacity: 0;
    transform: translateY(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
