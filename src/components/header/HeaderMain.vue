<script setup>
import HeaderContent from './HeaderContent.vue'
</script>
<template>
  <HeaderContent>
    <template #header-image="{ mobileImage, alt }">
      <img :src="mobileImage" :alt="alt" />
    </template>
    <template #header-content>
      <h1>The Bright Future of Web 3.0?</h1>
      <p>
        We dive into the next evolution of the web that claims to put the power of the platforms
        back into the hands of the people. But is it really fulfilling its promise?
      </p>
      <button>read more</button>
    </template>
  </HeaderContent>
</template>
<style lang="scss" scoped></style>
