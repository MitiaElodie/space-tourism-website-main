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
      <hr />
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
.destination-details {
   &__name {
      font-size: var(--h2-size);
   }

   &__description {
      margin-bottom: 2em;
   }

   &__additional-information {
      margin-top: 1em;
   }
}
</style>