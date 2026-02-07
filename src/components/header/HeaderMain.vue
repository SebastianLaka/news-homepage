<script setup>
import HeaderContent from './HeaderContent.vue';
</script>
<template>
<HeaderContent>
    <template #header-image="{mobileImage, alt}">
        <img :src="mobileImage" :alt="alt">
    </template>
</HeaderContent>
</template>
<style lang="scss" scoped>
</style>