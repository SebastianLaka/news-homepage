<script setup>
import { ref } from 'vue'
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
const toggleNavIcon = () => {
  isOpen.value = !isOpen.value
}
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
    <img :src="logoData.logo" :alt="logoData.alt" class="nav-main__logo" />
    <button @click="toggleNavIcon" class="nav-main__icon">
      <NavIcon :src="isOpen ? closeMobileIcon : mobileIcon" :alt="navIconLabel" />
    </button>
    <ul class="mobile-nav">
      <Navigation v-for="navItem in navItems" :key="navItem.id" :navItem="navItem.content" />
    </ul>
    <ul class="desktop-nav">
      <Navigation v-for="navItem in navItems" :key="navItem.id" :navItem="navItem.content" />
    </ul>
  </nav>
</template>
<style lang="scss" scoped>
@media (min-width: 375px) {
  .nav-main {
    display: flex;
    justify-content: space-between;
    align-items: center;
    &__icon {
      border: none;
    }
  }
}
</style>
