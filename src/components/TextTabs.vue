<script>
export default {
   props: {
      tabList: {
         type: Array,
         required: true,
      },

      initiallySelected: {
         type: String,
         default: null
      }
   },

   emits: ['click'],

   data() {
      return {
         selected: null,
      }
   },

   created() {
      this.selected = this.initiallySelected
   },

   methods: {
      onButtonClick(tabId) {
         this.$emit('click', tabId)
         this.selected = tabId
      }
   }
}
</script>

<template>
   <ul class="text-tabs__container">
      <li
         class="text-tabs__item"
         v-for="tab in tabList"
         :key="tab.id"
      >
         <button
            class="text-tabs__button"
            :class="{'text-tabs__button--selected': selected === tab.id}"
            @click="onButtonClick(tab.id)"
         >{{ tab.name }}</button>
      </li>
   </ul>
</template>

<style lang="scss">
.text-tabs {
   &__container {
      display: flex;
   }

   &__item {
      list-style: none;
   }

   &__button {
      background: none;
      color: var(--color-secondary-text);
      border: none;
      text-transform: uppercase;
      padding: 10px;

      &:hover {
         border-bottom: 2px solid var(--tab-border-bottom-hover-color);
      }

      &--selected,
      &--selected:hover {
         color: var(--color-text);
         border-bottom: 2px solid var(--tab-border-bottom-active-color);
      }
   }
}
</style>