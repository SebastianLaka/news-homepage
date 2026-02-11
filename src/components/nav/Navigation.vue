<script setup>
import { ref } from 'vue';
const props = defineProps({
  navItem: {
    type: String,
    required: true,
  },
})

</script>
<template>
  <li class="nav-item">
    <a href="#" class="nav-item__link">{{ props.navItem }}</a>
  </li>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/colors.scss' as *;
@use '../../assets/sass/fonts.scss' as *;
@use '../../assets/sass/breakpoints.scss' as *;
@media (min-width: $mobile-view) {
  .nav-item {
    list-style-type: none;
    &__link {
      text-decoration: none;
      color: getColor('very-dark-blue');
      font-size: 1.25rem;
      transition: color 0.3s ease-in-out;
      padding: 0.5em;
      &:hover {
        color: getColor('soft-red');
      }
    }
  }
}
@media (min-width: $desktop-small) {
  .nav-item {
    &__link {
      color: getColor('dark-grayish-blue');
      font-size: $main-size;
    }
  }
}
@media (min-width: $desktop-wide){
  .nav-item{
    &__link{
      padding: .5em .2em;
    }
    
  }
}
</style>
