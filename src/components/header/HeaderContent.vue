<script setup>
import { ref } from 'vue'
import MobileImageWeb from '../../assets/images/image-web-3-mobile.jpg'
import DesktopImageWeb from '../../assets/images/image-web-3-desktop.jpg'
const headerImage = ref({
  mobileImage: MobileImageWeb,
  desktopImage: DesktopImageWeb,
  alt: 'Header news image',
})
</script>
<template>
  <header class="news-header">
    <slot name="header-image" v-bind="headerImage" />
      <slot name="header-content" />
  </header>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/mixins.scss' as *;
@use '../../assets/sass/breakpoints.scss' as *;
@media (min-width: $mobile-view) {
  .news-header {
    margin-top: 4.5em;
    @include flex-layout($flex-direction: column);
    gap: 1.5em 0;
  }
}
@media (min-width: $desktop-small){
  .news-header{
    margin-top: 6.5em;
    grid-column: 1/9;
  }
}
@media (min-width: $desktop-wide){
  .news-header{
    grid-column: 2/9;
  }
}
</style>
