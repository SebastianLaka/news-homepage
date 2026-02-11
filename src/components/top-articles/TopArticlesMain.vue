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
  <article class="top-article-main">
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
  </article>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/mixins.scss' as *;
@use '../../assets//sass/fonts.scss' as *;
@use '../../assets/sass/colors.scss' as *;
@use '../../assets/sass/breakpoints.scss' as *;
@media (min-width: $mobile-view) {
  .top-article-main {
    @include flex-layout($flex-direction: column);
    gap: 1.5em 0;
    .top-article {
      @include flex-layout($align-items: stretch);
      gap: 0 1.5em;
      &__image {
        width: 100px; 
        height: 125px; 
        object-fit: cover;
 
      }
      .article-content {
        @include flex-layout($flex-direction: column, $justify-content: center);
        gap: .5em 0;
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
        &__about {
          max-width: 25ch;
        }
      }
    }
  }
}
@media (min-width: $desktop-small) {
  .top-article-main {
    grid-column: 1 / 13;
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 0 1.5em;
    .article-item-1 {
      grid-column: 1 / 5;
    }
    .article-item-2 {
      grid-column: 5 / 9;
    }
    .article-item-3 {
      grid-column: 9 / 13;
    }
  }
}
@media (min-width: $desktop-wide) {
  .top-article-main {
    grid-column: 2/12;
    gap: 0 5em;
    .top-article {
      .article-content {
        padding-right: 0;
      }
    }
  }
}
</style>
