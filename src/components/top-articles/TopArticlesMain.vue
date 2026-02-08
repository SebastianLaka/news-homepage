<script setup>
import { ref } from 'vue'
import TopArticles from './TopArticles.vue'
import retroPC from '../../assets/images/image-retro-pcs.jpg'
import laptops from '../../assets/images/image-top-laptops.jpg'
import gamingPad from '../../assets/images/image-gaming-growth.jpg'
const topArticles = ref([
  {
    id: 1,
    title: 'Reviving Retro PCs',
    description: 'What happens when old PCs are given modern upgrades?',
    image: retroPC,
    alt: 'Retro laptop img',
  },
  {
    id: 2,
    title: ' Top 10 Laptops of 2022',
    description: 'Our best picks for various needs and budgets.',
    image: laptops,
    alt: 'Laptop keyboard',
  },
  {
    id: 3,
    title: ' The Growth of Gaming',
    description: 'How the pandemic has sparked fresh opportunities.',
    image: gamingPad,
    alt: 'Gaming pad flip at hand',
  },
])
</script>
<template>
  <TopArticles
    v-for="topArticle in topArticles"
    :key="topArticle.id"
    :class="`article-item-${topArticle.id}`"
  >
    <template #top-articles :class="`item-${topArticle.id}`">
      <div class="top-article">
        <img :src="topArticle.image" :alt="topArticle.alt" class="top-article__image" />
        <div class="article-content">
          <h1 class="article-content__article-number">0{{ topArticle.id }}</h1>
          <h2 class="article-content__header">{{ topArticle.title }}</h2>
          <p class="article-content__about">{{ topArticle.description }}</p>
        </div>
      </div>
    </template>
  </TopArticles>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/mixins.scss' as *;
@use '../../assets//sass/fonts.scss' as *;
@use '../../assets/sass/colors.scss' as *;
@media (min-width: 375px) {
  .top-article {
    @include flex-layout($align-items: stretch);
    gap: 0 1.5em;
    &__image {
      object-fit: cover;
      max-width: 30%;
    }
    .article-content {
      @include flex-layout($flex-direction: column, $justify-content: center);
      gap: 1em 0;
      padding-right: 0.25em;
      &__article-number {
        color: getColor('soft-red');
        font-size: 2.25rem;
      }
      &__header {
        transition: color 0.3s ease-in-out;
        cursor: pointer;
        font-size: 1rem;
        &:hover {
          color: getColor('soft-red');
        }
      }
      &__about{
        max-width: 30ch;
      }
    }
  }
}
@media (min-width: 992px) {
  .top-article {
    gap: 0 1em;
    &__image {
      max-width: 35%;
    }
    .article-content{
        padding: 0;
        gap: 0;
    }
  }
  .article-item-1 {
    grid-column: 1 / 5;
    grid-row: 2/2;
  }
  .article-item-2 {
    grid-column: 5/9;
  }
  .article-item-3 {
    grid-column: 9/13;
  }
}
</style>
