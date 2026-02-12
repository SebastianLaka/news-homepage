<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import HeaderContent from './HeaderContent.vue'
const mobileSize = ref(false)
const checkScreen = () => {
  mobileSize.value = window.innerWidth <= 992
}
onMounted(() => {
  checkScreen()
  window.addEventListener('resize', checkScreen)
})
onUnmounted(() => {
  checkScreen()
  window.removeEventListener('resize', checkScreen)
})
</script>
<template>
  <HeaderContent>
    <template #header-image="{ mobileImage, desktopImage, alt }">
      <img :src="mobileSize ? mobileImage : desktopImage" :alt="alt" />
    </template>
    <template #header-content>
      <div class="news-header-content">
        <h1 class="news-header-content__header">The Bright Future of Web 3.0?</h1>
        <div class="header-content-description">
          <p class="header-content-description__description">
            We dive into the next evolution of the web that claims to put the power of the platforms
            back into the hands of the people. But is it really fulfilling its promise?
          </p>
          <button class="header-content-description__cta">read more</button>
        </div>
      </div>
    </template>
  </HeaderContent>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/mixins.scss' as *;
@use '../../assets//sass/fonts.scss' as *;
@use '../../assets/sass/colors.scss' as *;
@use '../../assets/sass/breakpoints.scss' as *;
@media (min-width: $mobile-view) {
  .news-header-content {
    @include flex-layout($flex-direction: column, $align-items: start);
    @include set-gap($row-gap: 0.75em);
    padding: 0 1em 0 0.5em;
    &__header {
      font-size: 3rem;
    }
    .header-content-description {
      @include flex-layout(
        $flex-direction: column,
        $justify-content: space-between,
        $align-items: start
      );
      @include set-gap($row-gap: 1.5em);
      height: 100%;
      &__description {
        max-width: 65ch;
      }
      &__cta {
        padding: 1em 2em;
        text-transform: uppercase;
        letter-spacing: 0.15em;
        font-weight: $bold-weight;
        border: none;
        background-color: getColor('soft-red');
        transition:
          background-color 0.3s ease-in-out,
          color 0.3s ease-in-out;
        &:hover {
          background-color: getColor('very-dark-blue');
          color: getColor('off-white');
        }
      }
    }
  }
}
@media (min-width: $desktop-small) {
  .news-header-content {
    @include grid-layout($columns: 2);
    @include set-gap($column-gap: 2em);
    padding: 0 0 0 0.5em;
    .header-content-description {
      @include grid-child(2,2);
      &__description {
        max-width: 40ch;
      }
    }
  }
}
@media (min-width: $desktop-wide) {
  .news-header-content {
    @include set-gap($column-gap: 0, $row-gap: 0);
    &__header {
      padding-right: 1em;
    }
  }
}
</style>
