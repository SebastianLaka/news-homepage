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
@media (min-width: 375px) {
  .news-header {
    padding-top: 4.5em;
    @include flex-layout($flex-direction: column);
    gap: 1.5em 0;
  }
}
@media (min-width: 992px){
  .news-header{
    grid-column: 1/8;
  }
}
@media (min-width: 1300px){
  .news-header{
    grid-column: 3/8;
  }
}
</style>
