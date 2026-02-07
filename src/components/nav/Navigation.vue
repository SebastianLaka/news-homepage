<script setup>
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
@media (min-width: 375px) {
  .nav-item {
    list-style-type: none;
    &__link {
      text-decoration: none;
      color: $very-dark-blue;
      font-size: 1.25rem;
    }
  }
}
@media (min-width: 992px){
.nav-item {
  &__link {
    color: $dark-grayish-blue;
    font-size: $main-size;
  }
}
}

</style>
