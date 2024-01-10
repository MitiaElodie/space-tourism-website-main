<script>
export default {
   props: {
      destination: {
         type: Object,
         required: true
      }
   }
}
</script>

<template>
   <div class="destination-details">
      <h2 class="destination-details__name">{{ destination.name }}</h2>
      <p class="destination-details__description">{{ destination.description }}</p>
      <div class="destination-details__additional-information">
         <div class="destination-details__distance-container">
            <span class="destination-details__label">Avg. distance</span>
            <span class="destination-details__value">{{ destination.distance }}</span>
         </div>
         <div class="destination-details__time-container">
            <span class="destination-details__label">Est. travel time</span>
            <span class="destination-details__value">{{ destination.travelTime }}</span>
         </div>
      </div>
   </div>
</template>

<style lang="scss">
@use '@/assets/base.scss';

.destination-details {
   text-align: center;
   &__name {
      font-size: var(--h2-size);
      margin: var(--destination-title-margin) 0;
   }

   &__description {
      padding-bottom: 2em;
      color: var(--color-secondary-text);
      border-bottom: 0.2px solid var(--destination-separator-color);
      font-size: var(--body-size);
      line-height: var(--body-line-height);
   }

   &__additional-information {
      display: flex;
      gap: 20px;
      flex-direction: column;
      margin-top: 1em;
      text-transform: uppercase;
   }

   &__label {
      display: block;
      margin-bottom: 0.5em;
      color: var(--color-secondary-text);
   }

   &__separator {
      color: var(--destination-separator-color)
   }
}


@media (min-width: base.$tablet-breakpoint) {
   .destination-details {
      &__additional-information {
         flex-direction: row;
         justify-content: center;
         gap: var(--destination-additional-information-gap);
      }
   }
}

@media (min-width: base.$laptop-breakpoint) {
   .destination-details {
      text-align: left;

      &__additional-information {
         justify-content: start;
      }
   }
}
</style>