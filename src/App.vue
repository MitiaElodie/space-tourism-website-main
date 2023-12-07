<script>
export default {
   watch: {
      $route(to) {
         // to update the background every time we change
         document.body.className = `body__${to.name}`
      }
   }
}
</script>
<template>
   <header class="app__header">
      <img class="app__logo" src="/img/shared/logo.svg" />
      <menu class="app__menu">
         <RouterLink class="app__router-link" :to="{ name: 'home' }">Home</RouterLink>
         <RouterLink class="app__router-link" :to="{ name: 'destination' }">Destination</RouterLink>
         <RouterLink class="app__router-link" :to="{ name: 'crew' }">Crew</RouterLink>
         <RouterLink class="app__router-link" :to="{ name: 'technology' }">Technology</RouterLink>
      </menu>
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

   &__header {
      display: flex;
      justify-content: space-between;
   }

   &__menu {
      display: flex;
      gap: 1.5em
   }

   &__router-link {
      text-decoration: none;
      text-transform: uppercase;
      color: var(--color-text);
      padding: 1em 0;

      &:hover {
         border-bottom: 3px solid var(--tab-border-bottom-hover-color);
      }

      &--active {
         border-bottom: 3px solid var(--tab-border-bottom-active-color);
      }
   }

   &__logo {
      height: var(--logo-size);
      width: var(--logo-size);
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