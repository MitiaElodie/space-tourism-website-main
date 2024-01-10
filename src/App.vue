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
         ],
         menuOpened: false,
         menuToggleIcon: '/img/shared/icon-hamburger.svg',
      }
   },

   watch: {
      $route(to) {
         // to update the background every time we change
         document.body.className = `body__${to.name}`
      }
   },

   methods: {
      onClickMenuToggle() {
         this.menuOpened = !this.menuOpened

         const iconName = this.menuOpened ? 'close' : 'hamburger'
         this.menuToggleIcon = '/img/shared/icon-'+ iconName +'.svg'
      }
   }
}
</script>
<template>
   <header class="app__header">
      <img class="app__logo" src="/img/shared/logo.svg" />
      <div class="app__horizontal-separator"/>
      <menu
         class="app__menu"
         :class="{'app__menu--closed': !this.menuOpened}"
      >
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
      <div
         class="app__menu-toggle"
         @click="onClickMenuToggle"
      >
         <img
            class="app__menu-toggle-icon"
            :src="menuToggleIcon"
         />
      </div>
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
      position: relative;

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

@media (max-width: base.$tablet-breakpoint) {
   .app {
      &__menu {
         position: absolute;
         flex-direction: column;
         width: 75%;
         height: 100vh;
         top: 0;
         right: 0;
         padding: 0 2em;
         padding-top: 150px;

         &--closed {
            display: none;
         }
      }

      &__router-link {
         padding: 20px;
      }

      &__menu-toggle {
         z-index: 2;
         padding: 20px;
      }
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

   .app {
      &__menu-toggle {
         display: none;
      }

      &__menu-number {
         display: none;
      }
   }
}

@media (min-width: base.$laptop-breakpoint) {
   .app {
      &__menu-number {
         display: inline-block;
      }

      &__horizontal-separator {
         height: 2px;
         width: 100%;
         margin-right: -1em;
         margin-left: 2em;
         z-index: 2;
         background-color: var(--menu-background-color);
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