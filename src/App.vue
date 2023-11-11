<template>
   <header>
      <RouterLink :to="{ name: 'home' }">Home</RouterLink>
      <RouterLink :to="{ name: 'destination' }">Destination</RouterLink>
      <RouterLink :to="{ name: 'crew' }">Crew</RouterLink>
      <RouterLink :to="{ name: 'technology' }">Technology</RouterLink>
   </header>
   <main class="app__main">
      <RouterView />
   </main>
</template>

<style lang="scss">
@use '@/assets/base.scss';

.app {
   --main-horizontal-padding: 24px;
   --main-vertical-padding: 40px;

   &__main {
      padding: var(--main-horizontal-padding) var(--main-vertical-padding);
   }
}

@media (min-width: base.$tablet-breakpoint) {
      .app {
         --main-horizontal-padding: 165px;
         --main-vertical-padding: 76px;
      }
   }

   @media (min-width: base.$laptop-breakpoint) {
      .app {
         --main-horizontal-padding: 165px;
         --main-vertical-padding: 76px;
      }
   }
</style>