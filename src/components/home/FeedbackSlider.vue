<template>
  <section class="reviews-marquee">
    <h5 class="title container">What our clients say</h5>
    <p class="subtitle container">
      Join thousands of satisfied clients who trust Aston VIP for their Dubai business journey
    </p>
    <div class="reviews-marquee__wrap">
      <div ref="trackTop" class="reviews-marquee__track">
        <div class="reviews-marquee__row">
          <article v-for="(item, i) in reviewsTopLoop" :key="'top-' + i" class="review-card">
            <p class="review-text">{{ item.text }}</p>
            <div class="review-bottom">
              <p class="review-author">{{ item.author }}</p>
              <div class="review-info">
                <span class="review-role">{{ item.role }}</span>
                <span v-if="item.icon" class="review-icon" v-html="item.icon"></span>
                <span class="review-role">{{ item.country }}</span>
              </div>
            </div>
          </article>
        </div>
      </div>

      <div ref="trackBottom" class="reviews-marquee__track">
        <div class="reviews-marquee__row">
          <article v-for="(item, i) in reviewsBottomLoop" :key="'bottom-' + i" class="review-card">
            <p class="review-text">{{ item.text }}</p>
            <div class="review-bottom">
              <p class="review-author">{{ item.author }}</p>
              <div class="review-info">
                <span class="review-role">{{ item.role }}</span>
                <span v-if="item.icon" class="review-icon" v-html="item.icon"></span>
                <span class="review-role">{{ item.country }}</span>
              </div>
            </div>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount } from 'vue'
import { gsap } from 'gsap'

const SPEED = 30

const trackTop = ref(null)
const trackBottom = ref(null)

const reviews = [
  {
    text: 'Aston VIP isn’t just a service-it’s a business partner. Highly recommended for anyone serious about success in Dubai.',
    author: 'Karim S.',
    role: 'FinTech CEO,',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 32 32"><path fill="#cc2b1d" d="M1 11H31V21H1z"></path><path d="M5,4H27c2.208,0,4,1.792,4,4v4H1v-4c0-2.208,1.792-4,4-4Z"></path><path d="M5,20H27c2.208,0,4,1.792,4,4v4H1v-4c0-2.208,1.792-4,4-4Z" transform="rotate(180 16 24)" fill="#f8d147"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>`,
    country: 'Germany',
  },
  {
    text: 'We saved weeks of time and a significant amount of money by using Aston VIP. They’re experts who truly care about their clients.',
    author: 'Ahmed R.',
    role: 'Investor,',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 32 32"><path fill="#fff" d="M1 11H31V21H1z"></path><path d="M5,4H27c2.208,0,4,1.792,4,4v4H1V8c0-2.208,1.792-4,4-4Z" fill="#be2a2c"></path><path d="M5,20H27c2.208,0,4,1.792,4,4v4H1v-4c0-2.208,1.792-4,4-4Z" transform="rotate(180 16 24)"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M18.5,18.367h0c-.036-.882-.138-3.253-.176-4.166-.13-1.044-1.131,.042-1.702-.052-.309-.439,.042-1.889-.819-1.503-.199-.039-.39-.096-.44,.074,0,0,0,0,0,0-.023,.079-.019,.178,.015,.15,0,0,0,0,0,0,.146-.12,.308,.051,.332,.197,0,0,0,0,0,0,0,.001,0,.002,0,.003,0-.001,0-.002,0-.003,.062,.286-.15,.856-.342,1.082-.567,.087-1.564-.988-1.692,.052,0,0,0,0,0,0l-.176,4.166h0s0,0,0,0l1.35-1.207-.289,1.025c-.1-.017-.192-.092-.28-.022-.158-.008-.23,.179-.176,.287,.007-.015,.021-.026,.037-.036-.023,.03-.038,.071-.038,.124-.136-.029-.167,.174-.268,.174,.087,.024,.021,.203,.18,.256,.265,.598,3.697,.602,3.965,0,.159-.053,.094-.232,.18-.256-.101,0-.133-.203-.268-.174,0-.053-.014-.093-.037-.124,.017,.009,.03,.02,.037,.036,.054-.108-.018-.295-.176-.287-.088-.07-.181,.005-.281,.022l-.289-1.025s1.349,1.205,1.351,1.207h0Z" fill="#c09300" fill-rule="evenodd"></path><path d="M18.184,18.709c-.008,0-.015,.001-.021,.003,.007,0,.014,0,.021-.003Z" fill="#c09300" fill-rule="evenodd"></path><path d="M13.837,18.712c-.006-.002-.013-.003-.021-.003,.007,.002,.015,.003,.021,.003Z" fill="#c09300" fill-rule="evenodd"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>`,
    country: 'Egypt',
  },
  {
    text: 'I had my bank account ready in just three days. Aston VIP handled everything—seamless and professional!',
    author: 'James T.',
    role: 'Entrepreneur,',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 32 32"><rect x="1" y="4" width="30" height="24" rx="4" ry="4" fill="#071b65"></rect><path d="M5.101,4h-.101c-1.981,0-3.615,1.444-3.933,3.334L26.899,28h.101c1.981,0,3.615-1.444,3.933-3.334L5.101,4Z" fill="#fff"></path><path d="M22.25,19h-2.5l9.934,7.947c.387-.353,.704-.777,.929-1.257l-8.363-6.691Z" fill="#b92932"></path><path d="M1.387,6.309l8.363,6.691h2.5L2.316,5.053c-.387,.353-.704,.777-.929,1.257Z" fill="#b92932"></path><path d="M5,28h.101L30.933,7.334c-.318-1.891-1.952-3.334-3.933-3.334h-.101L1.067,24.666c.318,1.891,1.952,3.334,3.933,3.334Z" fill="#fff"></path><rect x="13" y="4" width="6" height="24" fill="#fff"></rect><rect x="1" y="13" width="30" height="6" fill="#fff"></rect><rect x="14" y="4" width="4" height="24" fill="#b92932"></rect><rect x="14" y="1" width="4" height="30" transform="translate(32) rotate(90)" fill="#b92932"></rect><path d="M28.222,4.21l-9.222,7.376v1.414h.75l9.943-7.94c-.419-.384-.918-.671-1.471-.85Z" fill="#b92932"></path><path d="M2.328,26.957c.414,.374,.904,.656,1.447,.832l9.225-7.38v-1.408h-.75L2.328,26.957Z" fill="#b92932"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>`,
    country: 'UK',
  },
  {
    text: 'Opening a bank account in Dubai seemed impossible before I found Aston VIP. Their connections and knowledge are unmatched',
    author: 'Mark L.',
    role: 'CEO, tech startup,',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 32 32"><rect x="1" y="4" width="30" height="24" rx="4" ry="4" fill="#ac2431"></rect><path fill="#fff" d="M31 12L17 12 17 4 9 4 9 12 1 12 1 20 9 20 9 28 17 28 17 20 31 20 31 12z"></path><path fill="#061a57" d="M31 14L15 14 15 4 11 4 11 14 1 14 1 18 11 18 11 28 15 28 15 18 31 18 31 14z"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>`,
    country: 'Norway',
  },
  {
    text: 'Aston VIP’s 1-button setup was a game-changer for me. I couldn’t believe how simple the process was.',
    author: 'Sophia H.',
    role: 'Digital Nomad',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 32 32"><rect x="1" y="4" width="30" height="24" rx="4" ry="4" fill="#061b65"></rect><path d="M6.5,13.774v2.226h4v-2.227l3.037,2.227h2.463v-1.241l-3.762-2.759h3.762v-4h-2.74l2.74-2.009v-1.991h-1.441l-4.059,2.977v-2.977H6.5v2.794l-3.257-2.389c-.767,.374-1.389,.983-1.786,1.738l2.532,1.858H1s0,0,0,0v4h3.763l-3.763,2.76v1.24H3.464l3.036-2.226Z" fill="#fff"></path><path d="M1.805,5.589l3.285,2.411h1.364L2.359,4.995c-.204,.18-.39,.377-.554,.594Z" fill="#d22d32"></path><path fill="#d22d32" d="M1 16L6.454 12 6.454 13 2.363 16 1 16z"></path><path id="1705926025352-5861297_Star7" d="M6.838,18.741l.536,1.666,1.636-.62-.968,1.457,1.505,.893-1.743,.152,.24,1.733-1.205-1.268-1.205,1.268,.24-1.733-1.743-.152,1.505-.893-.968-1.457,1.636,.62,.536-1.666Z" fill="#fff"></path><path id="1705926025352-5861297_Star7-2" d="M23.113,21.755l.291,.906,.89-.337-.527,.793,.819,.486-.948,.082,.131,.943-.656-.69-.656,.69,.131-.943-.948-.082,.819-.486-.527-.793,.89,.337,.291-.906Z" fill="#fff"></path><path id="1705926025352-5861297_Star7-3" d="M20.166,13.127l.291,.906,.89-.337-.527,.793,.819,.486-.948,.082,.131,.943-.656-.69-.656,.69,.131-.943-.948-.082,.819-.486-.527-.793,.89,.337,.291-.906Z" fill="#fff"></path><path id="1705926025352-5861297_Star7-4" d="M23.43,7.127l.291,.906,.89-.337-.527,.793,.819,.486-.948,.082,.131,.943-.656-.69-.656,.69,.131-.943-.948-.082,.819-.486-.527-.793,.89,.337,.291-.906Z" fill="#fff"></path><path id="1705926025352-5861297_Star7-5" d="M28.132,10.817l.291,.906,.89-.337-.527,.793,.819,.486-.948,.082,.131,.943-.656-.69-.656,.69,.131-.943-.948-.082,.819-.486-.527-.793,.89,.337,.291-.906Z" fill="#fff"></path><path id="1705926025352-5861297_Star5" d="M25.742,16l.23,.565,.608,.045-.466,.393,.146,.592-.518-.321-.518,.321,.146-.592-.466-.393,.608-.045,.23-.565Z" fill="#fff"></path><path fill="#d22d32" d="M9.5 16L7.5 16 7.5 11 1 11 1 9 7.5 9 7.5 4 9.5 4 9.5 9 16 9 16 11 9.5 11 9.5 16z"></path><path fill="#d22d32" d="M16 15.667L11 12 11 13 15.091 16 16 16 16 15.667z"></path><path fill="#d22d32" d="M16 4L15.752 4 10.291 8.004 11.655 8.004 16 4.818 16 4z"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>`,
    country: 'Australia',
  },
  {
    text: 'The team at Aston VIP is knowledgeable, efficient, and always available to answer my questions.',
    author: 'Liam P.',
    role: 'Founder',
    icon: `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 32 32"><path fill="#fff" d="M10 4H22V28H10z"></path><path d="M5,4h6V28H5c-2.208,0-4-1.792-4-4V8c0-2.208,1.792-4,4-4Z" fill="#479a67"></path><path d="M25,4h6V28h-6c-2.208,0-4-1.792-4-4V8c0-2.208,1.792-4,4-4Z" transform="rotate(180 26 16)" fill="#ef8f4e"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>`,
    country: 'Ireland',
  },
]

const reviewsTopLoop = computed(() => [...reviews, ...reviews])
const reviewsBottomLoop = computed(() => [...reviews, ...reviews])

let destroyFns = []
let resizeTimeout = null

function createMarquee(trackEl, reverse = false) {
  const row = trackEl.querySelector('.reviews-marquee__row')
  if (!row) return null

  const fullWidth = row.scrollWidth
  if (!fullWidth) return null

  const cycleWidth = fullWidth / 2

  gsap.set(row, { x: 0 })

  const distance = reverse ? cycleWidth : -cycleWidth
  const duration = Math.abs(distance) / SPEED

  const tween = gsap.to(row, {
    x: reverse ? `+=${cycleWidth}` : `-=${cycleWidth}`,
    duration,
    ease: 'none',
    repeat: -1,
    modifiers: {
      x: (x) => {
        let val = parseFloat(x)
        const w = cycleWidth

        val = ((val + w) % w) - w
        return `${val}px`
      },
    },
  })

  const onEnter = () => {
    if (window.innerWidth >= 1024) {
      tween.pause()
    }
  }
  const onLeave = () => {
    tween.resume()
  }

  trackEl.addEventListener('mouseenter', onEnter)
  trackEl.addEventListener('mouseleave', onLeave)

  return () => {
    tween.kill()
    trackEl.removeEventListener('mouseenter', onEnter)
    trackEl.removeEventListener('mouseleave', onLeave)
  }
}

function setupMarquees() {
  destroyMarquees()

  if (trackTop.value) {
    const destroyTop = createMarquee(trackTop.value, false)
    if (destroyTop) destroyFns.push(destroyTop)
  }

  if (trackBottom.value) {
    const destroyBottom = createMarquee(trackBottom.value, true)
    if (destroyBottom) destroyFns.push(destroyBottom)
  }
}

function destroyMarquees() {
  destroyFns.forEach((fn) => fn && fn())
  destroyFns = []
}

function handleResize() {
  if (resizeTimeout) clearTimeout(resizeTimeout)
  resizeTimeout = setTimeout(() => {
    setupMarquees()
  }, 200)
}

onMounted(() => {
  setupMarquees()
  window.addEventListener('resize', handleResize)
})

onBeforeUnmount(() => {
  destroyMarquees()
  window.removeEventListener('resize', handleResize)
  if (resizeTimeout) clearTimeout(resizeTimeout)
})
</script>

<style scoped lang="scss">
.title {
  @include header;
  text-align: center;
  margin-top: 120px;
  margin-bottom: 20px;
  color: $black;
  @media (max-width: 760px) {
    margin-top: 64px;
    margin-bottom: 24px;
  }
}
.subtitle {
  font-size: 20px;
  text-align: center;
  margin-bottom: 102px;
  @media (max-width: 760px) {
    margin-bottom: 24px;
    font-size: 18px;
  }
}
.review-info {
  display: flex;
  align-items: center;
  gap: 5px;
}

.review-icon {
  display: flex;
  align-items: center;
}

.reviews-marquee {
  width: 100%;
  overflow: hidden;
  min-height: 442px;
  background-color: $grey;
  padding-bottom: 68px;
}

.reviews-marquee__wrap {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.reviews-marquee__track {
  /*overflow: hidden;*/
}

.reviews-marquee__row {
  display: flex;
  flex-wrap: nowrap;
  gap: 24px;
  will-change: transform;
}

/* картка відгуку */
.review-card {
  min-width: 500px;
  min-height: 250px;
  background: #ffffff;
  border-radius: 24px;
  padding: 32px;
  box-shadow: 0 5px 15px rgba(15, 23, 42, 0.08);

  display: flex;
  flex-direction: column;
  justify-content: space-between;
  /*flex: 0 0 auto;*/
  &:nth-child(even) {
    min-width: 370px;
  }
  @media (max-width: 760px) {
    min-width: 290px;
    &:nth-child(even) {
      min-width: 300px;
    }
  }
}

.review-text {
  font-size: 18px;
  color: $small-text;
  @media (max-width: 760px) {
    font-size: 16;
  }
}
.review-bottom {
  display: flex;
  flex-direction: column;
  align-items: end;
  //gap: 5px;
}

.review-author {
  font-weight: 500;
  color: $black;
}

.review-role {
  font-size: 14px;
  font-weight: 400;
  color: $small-text;
}

/* мобілка */
@media (max-width: 768px) {
  .review-card {
    width: 260px;
    padding: 20px;
  }
}
</style>
