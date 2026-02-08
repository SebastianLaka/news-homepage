<script setup>
import SiteNavigation from './nav/NavMain.vue'
import HeaderMain from './header/HeaderMain.vue';
import NewsMain from './news-articles/NewsMain.vue';
</script>
<template>
  <main class="main-content">
    <SiteNavigation />
    <HeaderMain />
    <NewsMain />
  </main>
</template>
<style scoped lang="scss">
@use '../assets/sass/fonts.scss' as *;
@use '../assets/sass/mixins.scss' as *;
.main-content {
  min-height: 100svh;
}
@media (min-width: 375px){
  .main-content{
    @include flex-layout($flex-direction: column);
    gap: 2em;
  }
}
@media (min-width: 992px){
  .main-content{
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-template-rows: repeat(2, 1fr);
 
  }
}
</style>
