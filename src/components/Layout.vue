<script setup>
import SiteNavigation from './nav/NavMain.vue'
</script>
<template>
  <main class="main-content">
    <SiteNavigation />
  </main>
</template>
<style scoped lang="scss">
@use '../assets/sass/fonts.scss' as *;
.main-content {
  min-height: 100svh;
}
</style>
