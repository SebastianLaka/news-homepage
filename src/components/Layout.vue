<script setup>
import SiteNavigation from './nav/NavMain.vue'
import HeaderMain from './header/HeaderMain.vue';
import NewsMain from './news-articles/NewsMain.vue';
import TopArticles from './top-articles/TopArticlesMain.vue';

</script>
<template>
  <main class="main-content">
    <SiteNavigation />
    <HeaderMain />
    <NewsMain/>
    <TopArticles />
  </main>
</template>
<style scoped lang="scss">
@use '../assets/sass/fonts.scss' as *;
@use '../assets/sass/mixins.scss' as *;
@use '../assets/sass/breakpoints.scss' as *;
.main-content {
  min-height: 100svh;
}
@media (min-width: $mobile-view){
  .main-content{
    @include flex-layout($flex-direction: column);
    @include set-gap($row-gap: 2em, $column-gap: 2em);
  }
}
@media (min-width: $desktop-small){
  .main-content{
    @include grid-layout($columns: 12);
    @include set-gap($row-gap: 1.5em, $column-gap: 1.5em);
  }
}
@media (min-width: $desktop-wide){
  .main-content{
    max-width: 1440px;
    width: 100%;
    margin: 0 auto;
  }
}
</style>
