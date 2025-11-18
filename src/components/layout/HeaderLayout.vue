<template>
  <header class="header" :class="{ 'header--scrolled': isScrolled }">
    <!-- Чорний верхній бар -->
    <div class="header__top" :class="{ 'header__top--hidden': isScrolled }">
      <div class="container header__top-wrapper">
        <div class="left">
          <span>Talk Now</span>

          <a href="https://t.me/ASTON_VIP" target="_blank">
            <img class="icon" src="/icons/telegram.svg" alt="Telegram" />
          </a>
          <a href="https://wa.me/+15557109807" target="_blank">
            <img class="icon" src="/icons/whatsapp.svg" alt="WhatsApp" />
          </a>
          <a
            href="https://signal.me/#eu/QX3SekfyqUW6PEkzrcteX8R0hYNSA-NXYUWrZxfTIRA8cWgPIrVF-oGjYE7KjcgP"
            target="_blank"
          >
            <img class="icon" src="/icons/signal.svg" alt="signal" />
          </a>

          <span class="online">
            <span class="dot"></span>
            Online
          </span>
        </div>

        <div class="right">
          <a class="link" href="tel:+97145182623">
            <img class="icon" src="/icons/phone.png" alt="signal" />
            +971 4 518 2623
          </a>
          <span class="divider"></span>
          <span>We call you back in 5 minutes, Mon-Fri 9:00-18:00 GMT+4</span>
        </div>
      </div>
    </div>

    <!-- Білий хедер -->
    <div class="header__main" :class="{ 'header__main-scrolled': isScrolled }">
      <div class="container header__main-wrapper">
        <!-- ДЕСКТОПНЕ МЕНЮ -->
        <nav class="nav">
          <img class="logo" src="@/assets/logo.png" alt="Logo" />
          <a class="nav_link" href="/">Business setup</a>
          <a class="nav_link" href="/">Professional services</a>
          <a class="nav_link" href="/">Other services</a>
          <a class="nav_link" href="/">Resources</a>
          <a class="nav_link" href="/">Crypto license</a>
        </nav>

        <div class="actions">
          <button class="btn btn-primary">Free consultation</button>
          <button class="btn btn-outline">
            <img class="icon-btn" src="/icons/phone.svg" alt="signal" />
            Book call
          </button>
        </div>

        <!--  MOBILE MENU  -->
        <div class="mobile__menu">
          <img class="logo" src="@/assets/logo.png" alt="Logo" />
          <button class="mobile-menu-btn" @click="isMenuOpen = true">Menu</button>
        </div>
      </div>
    </div>

    <!-- MOBILE MENU OVERLAY (ДОДАНО) -->
    <div class="mobile-menu" :class="{ open: isMenuOpen }">
      <div class="mobile-menu__header">
        <img src="@/assets/logo.png" class="logo" alt="logo" />
        <button class="close-btn" @click="isMenuOpen = false">×</button>
      </div>

      <div class="mobile-menu__grid">
        <a class="mobile-item" href="/">Business setup</a>
        <a class="mobile-item" href="/">Professional services</a>
        <a class="mobile-item" href="/">Other services</a>
        <a class="mobile-item" href="/">Resources</a>
        <a class="mobile-item" href="/">Crypto license</a>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted, watch } from 'vue'

const isScrolled = ref(false)
const isMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 0
}

onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

watch(isMenuOpen, (val) => {
  if (val) {
    document.body.classList.add('no-scroll')
  } else {
    document.body.classList.remove('no-scroll')
  }
})
</script>

<style scoped lang="scss">
.icon {
  transition: all 0.25s ease;

  &:hover {
    transform: scale(1.1);
    //filter: brightness(0) saturate(100%) invert(42%) sepia(92%) saturate(7266%) hue-rotate(1deg) brightness(104%) contrast(105%);
  }
  .icon-btn {
    transition: all 0.5s ease;
  }
}

.header {
  position: sticky;
  top: 0;
  z-index: 100;
  width: 100%;
  background: $white-color;
  transition: box-shadow 0.5s ease;
}

.header--scrolled {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

/* Чорний верхній бар */
.header__top {
  background: $black;
  overflow: hidden;
  max-height: 40px;
  padding: 6px 0px;
  opacity: 1;
  transition:
    max-height 0.5s ease,
    opacity 0.5s ease;
  display: flex;
  align-items: center;
  &-wrapper {
    display: flex;
    flex: 1;
    align-items: center;
    justify-content: space-between;
  }
}

.header__top--hidden {
  max-height: 0;
  opacity: 0;
  padding: 0;
}

/* Білий хедер */
.header__main {
  background: $white-color;
  padding-top: 9px;
  padding-bottom: 5px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  &-scrolled {
    border-bottom: 1px solid #e5e5e5;
  }
  &-wrapper {
    display: flex;
    gap: 16px;
    justify-content: space-between;
    flex: 1;
  }
}

/* Верхній бар */
.left,
.right {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  color: $white-color;
}

.online {
  background: #cfffc733;
  color: #7aff64;
  padding: 0px 10px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  gap: 4px;
  margin-left: 8px;

  .dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: #7aff64;
    animation: pulse 1.4s infinite ease-out;
  }
  @keyframes pulse {
    0% {
      transform: scale(0.9);
      opacity: 1;
    }
    70% {
      transform: scale(1.1);
      opacity: 0;
    }
    100% {
      transform: scale(0.9);
      opacity: 1;
    }
  }
}

.divider {
  width: 4px;
  height: 4px;
  border-radius: 50%;
  background: $white-color;
}

/* Білий хедер */
.logo {
  height: 57px;
  width: 57px;
  margin-right: 8px;
}

.nav {
  display: flex;
  gap: 28px;
  @media (max-width: 1200px) {
    gap: 16px;
  }
}
.nav_link {
  position: relative;
  font-weight: 500;
  color: $small-text;
  text-decoration: none;
  transition: color 0.25s ease;

  &::after {
    content: '';
    position: absolute;
    left: 50%;
    bottom: 0px;
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: $accent;
    opacity: 0;
    transform: translateX(-50%) scale(0.5);
    transition:
      opacity 0.5s ease,
      transform 0.5s ease;
  }

  &:hover {
    color: $accent;

    &::after {
      opacity: 1;
      transform: translateX(-50%) scale(1);
    }
  }
}
.actions {
  display: flex;
  gap: 8px;
}

.btn {
  border-radius: 4px;
  padding: 14px 35px;
  cursor: pointer;
  border: 1px solid transparent;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-size: 18px;
  transition: all 0.5s ease;
  @media (max-width: 1200px) {
    padding: 14px 15px;
  }
}

.btn-primary {
  background: $primary;
  color: #ffffff;
  font-weight: 500;
  &:hover {
    background-color: $black;
  }
}

.btn-outline {
  background: #ffffff;
  color: $primary;
  border-color: $primary;
  &:hover {
    color: $accent;
    border-color: $accent;
    .icon-btn {
      filter: brightness(0) saturate(100%) invert(42%) sepia(92%) saturate(7266%) hue-rotate(1deg)
        brightness(104%) contrast(105%);
    }
  }
}

.mobile__menu {
  display: none;
}

.mobile-menu-btn {
  display: none;
  border: 2px solid #001f54;
  padding: 6px 16px;
  font-size: 16px;
  border-radius: 10px;
  background: #ffffff;
  cursor: pointer;
  color: #001f54;
  transition: 0.3s;
}

.mobile-menu-btn:hover {
  background: #001f54;
  color: white;
}

@media (max-width: 1024px) {
  .nav,
  .actions,
  .header__top {
    display: none !important;
  }
  .header__main-wrapper {
  }

  .mobile-menu-btn,
  .mobile__menu {
    display: flex !important;
  }
  .mobile__menu {
    display: flex;
    flex: 1;
    align-items: center;
    justify-content: space-between;
  }
}

/* MOBILE MENU OVERLAY */
.mobile-menu {
  position: fixed;
  inset: 0;
  transform: translateX(100%);
  transition: 0.35s ease;
  z-index: 9999;
}

.mobile-menu.open {
  transform: translateX(0);
}

.mobile-menu__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: white;
  padding: 16px;
  padding-top: 16px;
  padding-left: 16px;
  padding-right: 16px;
}

.close-btn {
  background: white;
  border: 1px solid #001f54;
  width: 42px;
  height: 42px;
  border-radius: 8px;
  font-size: 30px;
  line-height: 1;
  cursor: pointer;
}

.mobile-menu__grid {
  background: #3d4752;
  padding: 24px;
  //margin-top: 24px;
  display: flex;
  flex-direction: column;
  gap: 14px;
  height: calc(100vh - 80px);
}

.mobile-item {
  background: white;
  border-radius: 14px;
  max-height: 60px;
  padding: 18px;
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  color: #001f54;
  font-weight: 600;
  border: 1px solid #d9e1ea;
}
@media (max-width: 1200px) {
}
</style>
