<script>
export default {
   methods: {
      onButtonClick() {
         // do nothing for now
         console.log('Explore button clicked')
      }
   }
}
</script>

<template>
   <button
      class="explore-button"
      @click="onButtonClick"
   >Explore</button>
</template>

<style lang="scss">
.explore-button {
   height: var(--explore-button-size);
   width: var(--explore-button-size);
   font-size: var(--explore-button-font-size);

   color: var(--explore-button-color);
   background-color: var(--explore-button-background-color);

   border-radius: 100%;
   border: none;
   cursor: pointer;

   text-transform: uppercase;

   transition: box-shadow 0.1s ease;

   &:hover {
      box-shadow: 0 0 0 var(--explore-button-shadow-width) var(--explore-button-shadow-color);
   }
}
</style>