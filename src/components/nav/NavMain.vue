<script setup>
import { ref } from 'vue'
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
</script>
<template>
  <nav class="nav-main">
    <img :src="logoData.logo" :alt="logoData.alt" class="nav-main__logo"/>
    <button @click="toggleNavIcon" class="nav-main__icon">
      <NavIcon :src="isOpen ? closeMobileIcon : mobileIcon" :alt="navIconLabel" />
    </button>
  </nav>
</template>
<style lang="scss" scoped>
@media (min-width: 375px) {
  .nav-main {
    display: flex;
    justify-content: space-between;
    &__icon{
        border: none;
    }
  }
}
</style>
