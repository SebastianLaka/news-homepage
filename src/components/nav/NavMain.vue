<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import Navigation from './Navigation.vue'
import mobileIcon from '../icons/icon-menu.svg'
import closeMobileIcon from '../icons/icon-menu-close.svg'
import logo from '../icons/logo.svg'
import NavIcon from './NavIcon.vue'
const logoData = ref({
  logo: logo,
  alt: 'Logo which contain upper case W letter and dot',
})
const navIconLabel = 'Mobile menu toggle'
const isOpen = ref(false)
const isMobile = ref(true)
const isDesktop = ref(false)
const toggleNavIcon = () => {
  isOpen.value = !isOpen.value
}

const windowWidth = ref(null)
const checkScreen = () => {
  windowWidth.value = window.innerWidth
  if (windowWidth.value <= 992) {
    isMobile.value = true
    isDesktop.value = false
  } else {
    isMobile.value = false
    isDesktop.value = true
    isOpen.value = false
  }
}
onMounted(() => {
  checkScreen()
  window.addEventListener('resize', checkScreen)
})

onUnmounted(() => {
  window.removeEventListener('resize', checkScreen)
})

const navItems = ref([
  { id: 1, content: 'Home' },
  { id: 2, content: 'New' },
  { id: 3, content: 'Popular' },
  { id: 4, content: 'Trending' },
  { id: 5, content: 'Categories' },
])
</script>
<template>
  <nav class="nav-main">
    <a href="#" class="nav-main__logo"><img :src="logoData.logo" :alt="logoData.alt" /></a>
    <button @click="toggleNavIcon" class="nav-main__icon" v-show="isMobile">
      <NavIcon :src="isOpen ? closeMobileIcon : mobileIcon" :alt="navIconLabel" />
    </button>
    <Transition name="slide">
      <ul class="mobile-nav" v-show="isOpen">
        <Navigation v-for="navItem in navItems" :key="navItem.id" :navItem="navItem.content" />
      </ul>
    </Transition>
    <ul class="desktop-nav" v-show="isDesktop">
      <Navigation v-for="navItem in navItems" :key="navItem.id" :navItem="navItem.content" />
    </ul>
  </nav>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/colors.scss' as *;
@use '../../assets/sass/mixins.scss' as *;
@media (min-width: 375px) {
  .nav-main {
    @include flex-layout($flex-direction: row , $justify-content: space-between, $align-items: center);
    position: fixed;
    z-index: 10;
    left: 0;
    right: 0;
    padding: 1em;
    &__icon {
      border: none;
    }
    .mobile-nav {
      @include flex-layout($flex-direction: column, $justify-content: center);
      gap: 1em 0;
      position: absolute;
      top: 0;
      bottom: 0;
      left: 25%;
      right: 0;
      background-color: getColor('off-white');
      height: 100svh;
      z-index: -1;
    }
    .slide-enter-active,
    .slide-leave-active {
      transition: all 0.5s ease-in-out;
    }
    .slide-enter-from,
    .slide-leave-to {
      transform: translateX(1000px);
      opacity: 0;
    }
  }
}
@media (min-width: 992px) {
  .nav-main {
    .desktop-nav {
      @include flex-layout();
      gap: 0 2em;
    }
  }
}
@media (min-width: 1300px) {
  .nav-main {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    padding: 1em 0;
    &__logo {
      grid-column: 3/4;
    }
    .desktop-nav {
      grid-column: 8/13;
    }
  }
}
</style>
