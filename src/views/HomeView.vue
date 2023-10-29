<script>
import ExploreButton from '@/components/ExploreButton.vue';

export default {
   components: { ExploreButton }
}
</script>

<template>
   <div class="home-view">
      <section class="home-view__description">
         <span class="home-view__intro">
            So, you want to travel to
         </span>
         <h1 class="home-view__title">Space</h1>
         <p class="home-view__details">
            Let’s face it; if you want to go to space, you might as well genuinely go to outer space and not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly out of this world experience!
         </p>
      </section>
      <section class="home-view__explore-button-container">
         <ExploreButton />
      </section>
   </div>
</template>

<style lang="scss">
@use '@/assets/base.scss';

.home-view {
   &__explore-button-container,
   &__description {
      text-align: center;
   }

   &__intro {
      text-transform: uppercase;
      font-size: var(--h5-size);
   }

   &__title {
      text-transform: uppercase;
      padding-top: 0; // to remove the big gap
      font-size: var(--h1-size);
   }

   &__details {
      line-height: var(--body-line-height);
      font-size: var(--body-size);
   }

   --description-margin-bottom: 40px;
   &__description {
      margin-bottom: var(--description-margin-bottom);
   }
}

@media (min-width: base.$tablet-breakpoint) {
   .home-view {
      --description-margin-bottom: 60px;
   }
}

@media (min-width: base.$laptop-breakpoint) {
   .home-view {
      display: flex;
      gap: 20px;

      &__explore-button-container,
      &__description {
         text-align: start;
      }
   }
}
</style>
