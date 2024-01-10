<script>
export default {
   props: {
      order: {
         type: String,
         required: true,
      },

      title: {
         type: String,
         required: true,
      }
   }
}
</script>
<template>
   <div class="page-base">
      <h1 class="page-base__title-container">
         <span class="page-base__order">{{ order }}</span>
         <span class="page-base__title">{{ title }}</span>
      </h1>
      <slot />
   </div>
</template>

<style lang="scss">
@use '@/assets/base.scss';

.page-base {
   &__title-container {
      text-align: center;
      margin-bottom: var(--page-title-margin-bottom);
   }

   &__order {
      font-weight: 700;
      margin-right: 0.5em;
      color: var(--page-title-number-color);
   }

   &__title {
      text-transform: uppercase;
   }
}

@media (min-width: base.$tablet-breakpoint) {
   .page-base {
      &__title-container {
         text-align: left;
      }
   }
}
</style>