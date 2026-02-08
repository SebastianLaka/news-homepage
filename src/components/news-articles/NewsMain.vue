<script setup>
import { ref } from 'vue'
import NewsArticles from './NewsArticles.vue'
const newsTopics = ref([
  {
    id: 1,
    title: 'Hydrogen VS Electric Cars',
    description: ' Will hydrogen-fueled cars ever catch up to EVs?',
  },
  {
    id: 2,
    title: 'The Downsides of AI Artistry',
    description: 'What are the possible adverse effects of on-demand AI image generation?',
  },
  {
    id: 3,
    title: ' Is VC Funding Drying Up?',
    description: ' Private funding by VC firms is down 50% YOY. We take a look at what that means.',
  },
])
</script>
<template>
  <article class="news-articles">
    <h1 class="news-articles__header">New</h1>
    <NewsArticles v-for="newTopic in newsTopics" :key="newTopic.id">
      <template #news-topics>
        <div class="new-article-topic">
          <h1 class="new-article-topic__header">{{ newTopic.title }}</h1>
          <p class="new-article-topic__description">{{ newTopic.description }}</p>
        </div>
      </template>
    </NewsArticles>
  </article>
</template>
<style lang="scss" scoped>
@use '../../assets/sass/mixins.scss' as *;
@use '../../assets//sass/fonts.scss' as *;
@use '../../assets/sass/colors.scss' as *;
@media (min-width: 375px) {
  .news-articles {
    @include flex-layout($flex-direction: column, $justify-content: space-evenly);
    background-color: getColor('very-dark-blue');
    padding: 1.5em;
    gap: 1.5em 0;
    &__header {
      color: getColor('soft-orange');
    }
    .new-article-topic {
      @include flex-layout($flex-direction: column);
      gap: 0.75em 0;
      border-bottom: 0.1em solid white;
      &:last-child {
        border-bottom: none;
        padding: 0;
      }
      &__header {
        color: getColor('off-white');
        font-size: 1.1rem;
        cursor: pointer;
        transition: color .3s ease-in-out;
        &:hover {
          color: getColor('soft-orange');
        }
      }
      &__description {
        padding-bottom: 1.85em;
        color: getColor('grayish-blue');
      }
    }
  }
}
@media (min-width: 992px) {
  .news-articles {
    padding-top: 5.5em;
    grid-column: 8 / 13;
  }
}
@media (min-width: 1300px) {
  .news-articles {
    grid-column: 8/11;
  }
}
</style>
