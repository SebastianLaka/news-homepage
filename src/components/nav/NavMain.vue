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
const itemHover = ref(false)
const enterNavItem = (content) => {
  itemHover.value = content
}
const leaveNavItem = () => {
  itemHover.value = false
}
</script>
<template>
  <nav class="nav-main">
    <a href="#" class="nav-main__logo"><img :src="logoData.logo" :alt="logoData.alt" /></a>
    <button @click="toggleNavIcon" class="nav-main__icon" v-show="isMobile">
      <NavIcon :src="isOpen ? closeMobileIcon : mobileIcon" :alt="navIconLabel" />
    </button>
    <Transition name="slide">
      <ul class="mobile-nav site-navigation" v-show="isOpen">
        <Navigation
          v-for="navItem in navItems"
          :key="navItem.id"
          :navItem="navItem.content"
          @click="getNavItem(navItem)"
        />
      </ul>
    </Transition>
    <Transition name="slide-overlay">
      <div v-show="isOpen" class="nav-overlay" @click="isOpen = false"></div>
    </Transition>
    <ul class="desktop-nav site-navigation" v-show="isDesktop">
      <Navigation
        v-for="navItem in navItems"
        :key="navItem.id"
        :navItem="navItem.content"
        :isHover="itemHover === navItem.content"
        @mouseenter="enterNavItem(navItem.content)"
        @mouseleave="leaveNavItem"
        :class="[{ 'is-hover': itemHover === navItem.content }]"
      />
    </ul>
  </nav>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/colors.scss' as *;
@use '../../assets/sass/mixins.scss' as *;
@use '../../assets/sass/breakpoints.scss' as *;
@media (min-width: $mobile-view) {
  .nav-main {
    @include flex-layout(
      $flex-direction: row,
      $justify-content: space-between,
      $align-items: center
    );

    @include position-element($position: fixed, $right: 0, $left: 0, $z-index: 10);
    padding: 1em;
    background-color: getColor('off-white');
    &__icon {
      border: none;
    }
    .mobile-nav {
      @include flex-layout($flex-direction: column, $justify-content: center);
      @include set-gap($row-gap: 2em);
      padding: 1em;
      @include position-element(
        $position: absolute,
        $top: 0,
        $right: 0,
        $bottom: 0,
        $left: 25%,
        $z-index: -1
      );
      background-color: getColor('off-white');
      height: 100svh;
    }

    .slide-enter-active,
    .slide-leave-active {
      transition: all 0.5s ease-in-out;
    }
    .slide-enter-from,
    .slide-leave-to {
      transform: translateX(100%);
      opacity: 0;
    }
    .slide-overlay-enter-active,
    .slide-overlay-leave-active {
      transition: all 0.3s ease-in-out;
    }
    .slide-overlay-enter-from,
    .slide-overlay-leave-to {
      opacity: 0;
    }

    .nav-overlay {
      @include position-element(
        $position: fixed,
        $top: 0,
        $right: 0,
        $bottom: 0,
        $left: 0,
        $z-index: -10
      );
      background-color: rgba(0, 0, 0, 0.5);
    }
  }
}
@media (min-width: $desktop-small) {
  .nav-main {
    .desktop-nav {
      @include flex-layout();
      @include set-gap($column-gap: 2em);
      :deep(.is-hover) {
        .nav-item__link {
          color: getColor('soft-red');
        }
      }
    }
  }
}
@media (min-width: $desktop-wide) {
  .nav-main {
    @include grid-layout($columns: 12);
    padding: 1em 0;
    &__logo {
      @include grid-child(2, 4);
    }
    .desktop-nav {
      @include grid-child(7, 12);
      justify-self: end;
      @include set-gap($column-gap: 2em);
    }
  }
}
@media (min-width: $desktop-ultra-wide) {
  .nav-main {
    max-width: 1440px;
    width: 100%;
    margin: 0 auto;
  }
}
</style>
