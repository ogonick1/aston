<template>
  <section class="logos-marquee">
    <div ref="wrap" class="logos-marquee__wrap" aria-label="Logos carousel">
      <div ref="track" class="logos-marquee__track">
        <div class="logos-marquee__row">
          <article v-for="(logo, index) in logos" :key="index" class="logos-marquee__item">
            <div class="logos-marquee__card">
              <img :src="logo.src" :alt="logo.alt" class="logos-marquee__image" />
            </div>
          </article>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref } from 'vue'

const SPEED_PX_PER_SEC = 25

const wrap = ref(null)
const track = ref(null)

const logos = [
  { src: '/dmcc.png', alt: 'DMCC' },
  { src: '/ifza.png', alt: 'IFZA' },
  { src: '/dubai-economy.png', alt: 'Dubai Economy' },
  { src: '/uae.png', alt: 'UAE' },
  { src: '/dmcc.png', alt: 'DMCC' },
  { src: '/ifza.png', alt: 'IFZA' },
  { src: '/dubai-economy.png', alt: 'Dubai Economy' },
  { src: '/uae.png', alt: 'UAE' },
]

onMounted(() => {
  const w = wrap.value
  const t = track.value

  if (!w || !t) return

  const firstRow = t.firstElementChild
  if (!firstRow) return

  const clone = firstRow.cloneNode(true)
  clone.setAttribute('aria-hidden', 'true')
  t.appendChild(clone)

  let x = 0
  let paused = false
  let raf = 0
  let last = performance.now()

  const getHalf = () => firstRow.scrollWidth

  const step = (now) => {
    const dt = (now - last) / 1000
    last = now

    if (!paused) {
      x -= SPEED_PX_PER_SEC * dt
      const half = getHalf()
      if (half > 0 && -x >= half) {
        x += half
      }
      t.style.transform = `translateX(${x}px)`
    }

    raf = requestAnimationFrame(step)
  }

  const onMouseEnter = () => {
    paused = true
  }
  const onMouseLeave = () => {
    paused = false
  }

  w.addEventListener('mouseenter', onMouseEnter)
  w.addEventListener('mouseleave', onMouseLeave)

  const onResize = () => {
    x = 0
    t.style.transform = 'translateX(0px)'
  }

  window.addEventListener('resize', onResize)

  raf = requestAnimationFrame(step)

  onBeforeUnmount(() => {
    cancelAnimationFrame(raf)
    w.removeEventListener('mouseenter', onMouseEnter)
    w.removeEventListener('mouseleave', onMouseLeave)
    window.removeEventListener('resize', onResize)
  })
})
</script>

<style scoped>
.logos-marquee {
  position: relative;
  margin-bottom: 66px;
  margin-top: 66px;
}

@media (min-width: 640px) {
  .logos-marquee {
    margin-bottom: 40px;
    margin-top: 40px;
  }
}

.logos-marquee__wrap {
  position: relative;
  margin: 0 auto;
  width: 100%;
  overflow: hidden;
  padding: 4px 8px;
}

.logos-marquee__track {
  display: flex;
  gap: 16px;
  will-change: transform;
}

.logos-marquee__row {
  display: flex;
  gap: 40px;
}

.logos-marquee__item {
  flex-shrink: 0;
}

.logos-marquee__card {
  width: 152px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease,
    border-color 0.2s ease;
  overflow: hidden;
}

.logos-marquee__image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}
</style>
