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
@use '@/assets/function.scss';

.app {
   &__main {
      padding: var(--main-horizontal-padding) var(--main-vertical-padding);
   }

   &__header {
      display: flex;
      justify-content: space-between;
      align-items: center;

      padding-top: var(--header-margin-top);
   }

   &__menu {
      display: flex;
      gap: 1.5em;
      backdrop-filter: blur(4px);
      background-color: var(--menu-background-color);
      padding: 0 var(--menu-padding);
      height: var(--header-height);
   }

   &__router-link {
      display: flex;
      align-items: center;
      height: 100%;
      text-decoration: none;
      text-transform: uppercase;
      color: var(--color-text);
      border-bottom: 3px solid transparent;

      &:hover {
         border-bottom-color: var(--tab-border-bottom-hover-color);
      }

      &--active {
         border-bottom-color: var(--tab-border-bottom-active-color);
      }
   }

   &__logo {
      height: var(--logo-size);
      width: var(--logo-size);
      margin-left: var(--logo-margin-left);
   }

   &__menu-number {
      font-weight: 700;
      margin-right: 0.75em;
      display: none;
   }
}

.body {
   &__home {
      background-image: url(function.generateBodyBackgroundUrl('home','mobile'));
   }

   &__destination {
     background-image: url(function.generateBodyBackgroundUrl('destination','mobile'));
   }

   &__crew {
      background-image: url(function.generateBodyBackgroundUrl('crew','mobile'));
   }

   &__technology {
      background-image: url(function.generateBodyBackgroundUrl('technology','mobile'));
   }
}

@media (min-width: base.$tablet-breakpoint) {
  .body {
      &__home {
         background-image: url(function.generateBodyBackgroundUrl('home','tablet'));
      }

      &__destination {
         background-image: url(function.generateBodyBackgroundUrl('destination','tablet'));
      }

      &__crew {
         background-image: url(function.generateBodyBackgroundUrl('crew','tablet'));
      }

      &__technology {
         background-image: url(function.generateBodyBackgroundUrl('technology','tablet'));
      }
  }
}

@media (min-width: base.$laptop-breakpoint) {
   .app {
      &__menu-number {
         display: inline-block;
      }
   }

  .body {
      &__home {
         background-image: url(function.generateBodyBackgroundUrl('home','desktop'));
      }

      &__destination {
         background-image: url(function.generateBodyBackgroundUrl('destination','desktop'));
      }

      &__crew {
         background-image: url(function.generateBodyBackgroundUrl('crew','desktop'));
      }

      &__technology {
         background-image: url(function.generateBodyBackgroundUrl('technology','desktop'));
      }
   }
}
</style>