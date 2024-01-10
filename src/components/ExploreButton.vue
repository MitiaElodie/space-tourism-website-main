<template>
   <router-link
      class="explore-button"
      :to="{ name: 'destination' }"
   >Explore</router-link>
</template>

<style lang="scss">
.explore-button {
   display: flex;
   justify-content: center;
   align-items: center;

   height: var(--explore-button-size);
   width: var(--explore-button-size);
   font-size: var(--explore-button-font-size);

   color: var(--explore-button-color);
   background-color: var(--explore-button-background-color);

   border-radius: 100%;
   border: none;
   cursor: pointer;

   text-transform: uppercase;
   text-decoration: none;

   transition: box-shadow 0.1s ease;

   &:hover {
      box-shadow: 0 0 0 var(--explore-button-shadow-width) var(--explore-button-shadow-color);
   }
}
</style>