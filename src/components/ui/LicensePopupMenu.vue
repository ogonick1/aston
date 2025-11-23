<template>
  <transition name="license-popup-fade">
    <div
      v-if="visible"
      ref="popupRef"
      class="license-popup"
      :class="{ 'license-popup--collapsed': isCollapsed }"
      :style="popupStyle"
    >
      <header
        class="license-popup__header"
        @click="toggleCollapsed"
      >
        <div class="license-popup__icon">
          <img src="/icons/license-menu.svg" alt="" />
        </div>

        <div class="license-popup__title">
          License categories DIFC
        </div>

        <div
          class="license-popup__drag"
          @click.stop
          @mousedown.stop="startDrag"
          @touchstart.prevent.stop="startDrag"
        >
          <!--<img src="/icons/drag-handle.svg" alt="Drag" />-->
        </div>
      </header>

      <div class="license-popup__content">
        <div
          v-for="item in items"
          :key="item.id"
          class="license-popup__item"
          :class="{ 'license-popup__item--active': item.id === activeId }"
          @click="$emit('select', item)"
        >
          <div class="license-popup__item-badge">
            {{ item.badge }}
          </div>
          <div class="license-popup__item-title">
            {{ item.title }}
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import {
  ref,
  reactive,
  computed,
  onMounted,
  onBeforeUnmount,
} from 'vue'

const props = defineProps({
  items: {
    type: Array,
    default: () => [],
  },
  activeId: {
    type: [String, Number, null],
    default: null,
  },
  startX: {
    type: Number,
    default: 20,
  },
  startY: {
    type: Number,
    default: 150,
  },
})

const popupRef = ref(null)
const visible = ref(true)

const isCollapsed = ref(false)

const expandScrollStart = ref(0)

const position = reactive({
  x: props.startX,
  y: props.startY,
})

const popupSize = reactive({
  width: 0,
  height: 0,
})

const dragOffset = reactive({
  x: 0,
  y: 0,
})

const dragging = ref(false)

const popupStyle = computed(() => ({
  transform: `translate3d(${position.x}px, ${position.y}px, 0)`,
}))

function startDrag(event) {
  dragging.value = true
  document.body.classList.add("dragging")

  const rect = popupRef.value?.getBoundingClientRect()
  if (rect) {
    popupSize.width = rect.width
    popupSize.height = rect.height
  }

  const point = getPoint(event)
  dragOffset.x = point.x - position.x
  dragOffset.y = point.y - position.y
}

function handleMove(event) {
  if (!dragging.value) return

  const point = getPoint(event)

  let nextX = point.x - dragOffset.x
  let nextY = point.y - dragOffset.y

  const margin = 8
  const HEADER_HEIGHT = 65

  const maxX = window.innerWidth - popupSize.width - margin
  const maxY = window.innerHeight - popupSize.height - margin

  nextY = Math.max(nextY, HEADER_HEIGHT + margin)

  position.x = clamp(nextX, margin, Math.max(maxX, margin))
  position.y = clamp(
    nextY,
    HEADER_HEIGHT + margin,
    Math.max(maxY, HEADER_HEIGHT + margin),
  )

  if (event.type === 'touchmove') {
    event.preventDefault()
  }
}

function stopDrag() {
  dragging.value = false
  document.body.classList.remove("dragging")
}

function getPoint(event) {
  if (event.touches && event.touches[0]) {
    return {
      x: event.touches[0].clientX,
      y: event.touches[0].clientY,
    }
  }
  return {
    x: event.clientX,
    y: event.clientY,
  }
}

function clamp(value, min, max) {
  return Math.min(Math.max(value, min), max)
}

function toggleCollapsed() {
  isCollapsed.value = !isCollapsed.value

  if (!isCollapsed.value) {
    expandScrollStart.value =
      window.scrollY || window.pageYOffset || 0
  }
}

function handleScroll() {
  if (isCollapsed.value) return

  const current = window.scrollY || window.pageYOffset || 0
  const delta = current - expandScrollStart.value
  const threshold = window.innerHeight * 0.7 // скільки «пройти» після розгортання

  if (delta > threshold) {
    isCollapsed.value = true
  }
}

onMounted(() => {
  window.addEventListener('mousemove', handleMove)
  window.addEventListener('touchmove', handleMove, { passive: false })
  window.addEventListener('mouseup', stopDrag)
  window.addEventListener('touchend', stopDrag)

  expandScrollStart.value =
    window.scrollY || window.pageYOffset || 0

  window.addEventListener('scroll', handleScroll, { passive: true })
})

onBeforeUnmount(() => {
  window.removeEventListener('mousemove', handleMove)
  window.removeEventListener('touchmove', handleMove)
  window.removeEventListener('mouseup', stopDrag)
  window.removeEventListener('touchend', stopDrag)

  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped lang="scss">
.license-popup {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 9999;
  padding: 16px 8px 8px 8px;

  width: 280px;
  border-radius: 16px;
  background: #353E4E;
  overflow: hidden;
  transition:
    transform 0.03s linear,
    border-radius 0.2s ease,
    width 0.2s ease,
    height 0.2s ease;
    @media (max-width: 767px) {
      display: none;
    }
}

.license-popup-fade-enter-active,
.license-popup-fade-leave-active {
  transition: opacity 0.2s ease, transform 0.2s ease;
}
.license-popup-fade-enter-from,
.license-popup-fade-leave-to {
  opacity: 0;
  transform: translate3d(20px, 80px, 0) scale(0.95);
}

.license-popup__header {
  display: flex;
  align-items: center;
  gap: 12px;
  cursor: pointer;
}


.license-popup__icon {
  width: 20px;
  height: 20px;
  img {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
}

.license-popup__title {
  flex: 1;
  font-size: 16px;
  font-family: 'PTSerif';
  font-weight: 700;
  color: #fff;
}

/* DRAG HANDLE */
.license-popup__drag {
  border: none;
  background-image:url('/icons/drag-handle.svg');
  background-repeat: no-repeat;
  background-position: center;
  width: 26px;
  height: 26px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: grab;
}

.license-popup__drag:active {
  cursor: grabbing;
}

.license-popup__drag {
  width: 20px;
  height: 20px;
  display: block;
}

.license-popup__content {
  max-height: 80vh;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  gap: 4px;
  margin-top: 16px;
}

/* item */
.license-popup__item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px;
  border-radius: 12px;
  background: $black;
  color: #CAD8EF;
  cursor: pointer;
  border: 1px solid transparent;
  transition:
    background 0.15s ease,
    border-color 0.15s ease,
    box-shadow 0.15s ease;
}

.license-popup__item + .license-popup__item {
}

.license-popup__item:hover {
  background: #02081b;
  border-color: rgba(148, 163, 184, 0.3);
}

.license-popup__item--active {
  border-color: #FF8F4B;
  box-shadow: 0 0 0 1px rgba(249, 115, 22, 0.4);
}

.license-popup__item-badge {
  min-width: 28px;
  height: 28px;
  border-radius: 99px;
  background: #353E4E;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
}

.license-popup__item--active .license-popup__item-badge  {
  color: #FF8F4B;
}
.license-popup__item--active {
  .license-popup__item-title {
    color: #FF8F4B;
  }
}

.license-popup__item-title {
  font-size: 13px;
  font-weight: 700;
}

.license-popup--collapsed {
  padding: 16px;
  //border-radius: 999px;
}

.license-popup--collapsed .license-popup__content {
  display: none;
}



</style>
