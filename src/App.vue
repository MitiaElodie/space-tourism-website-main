<script>
export default {
   data() {
      return {
         menuList: [
            {
               number: '00',
               name: 'home',
            },
            {
               number: '01',
               name: 'destination',
            },
            {
               number: '02',
               name: 'crew',
            },
            {
               number: '03',
               name: 'technology',
            },
         ]
      }
   },

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
         <RouterLink
            v-for="menu in menuList"
            :key="menu.name"
            class="app__router-link"
            :to="{ name: menu.name }"
         >
            <span class="app__menu-number">{{ menu.number }}</span>
            <span class="app__menu-label">{{ menu.name }}</span>
         </RouterLink>
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
      gap: 1.5em;
      backdrop-filter: blur(10px);
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

   &__menu-number {
      font-weight: 700;
      margin-right: 0.75em;
      display: none;
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

      &__menu-number {
         display: inline-block;
      }
   }
}
</style>