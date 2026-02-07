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
    <div class="news-header-content">
      <slot name="header-content" />
    </div>
  </header>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/mixins.scss' as *;
@media (min-width: 375px) {
  .news-header {
    padding-top: 4.5em;
    @include flex-layout($flex-direction: column);
    gap: 1.5em 0;
    .news-header-content {
      @include flex-layout($flex-direction: column);
      gap: 1em 0;
    }
  }
}
</style>
