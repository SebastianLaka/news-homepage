<script setup>
import SiteNavigation from './nav/NavMain.vue'
import HeaderMain from './header/HeaderMain.vue';
</script>
<template>
  <main class="main-content">
    <SiteNavigation />
    <HeaderMain />
  </main>
</template>
<style scoped lang="scss">
@use '../assets/sass/fonts.scss' as *;
.main-content {
  min-height: 100svh;
}
@media (min-width: 992px){
  .main-content{
    display: grid;
    grid-template-columns: repeat(12, 1fr);
  }
}
</style>
