<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import HeaderContent from './HeaderContent.vue';
const mobileSize = ref(false);
const checkScreen = () => {
  mobileSize.value = window.innerWidth <= 992;
}
onMounted(() => {
  checkScreen();
  window.addEventListener('resize', checkScreen);
})
onUnmounted(() => {
  checkScreen();
  window.removeEventListener('resize', checkScreen);
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
        <p class="news-header-content__description">
          We dive into the next evolution of the web that claims to put the power of the platforms
          back into the hands of the people. But is it really fulfilling its promise?
        </p>
        <button class="news-header-content__cta">read more</button>
      </div>
    </template>
  </HeaderContent>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/mixins.scss' as *;
@use '../../assets//sass/fonts.scss' as *;
@use '../../assets/sass/colors.scss' as *;
@media (min-width: 375px) {
  .news-header-content {
    @include flex-layout($flex-direction: column, $align-items: start);
    gap: 0.75em 0;
    padding: 0 1em 0 .5em;
    &__header {
      font-size: 3rem;
    }
    &__description {
      max-width: 50ch;
    }
    &__cta {
      padding: 1em 2em;
      text-transform: uppercase;
      letter-spacing: 0.15em;
      font-weight: $bold-weight;
      border: none;
      background-color: getColor('soft-red');
      transition: background-color 0.3s ease-in-out, color .3s ease-in-out;
      &:hover {
        background-color: getColor('very-dark-blue');
        color: getColor('off-white');
      }
    }
  }
}
</style>
