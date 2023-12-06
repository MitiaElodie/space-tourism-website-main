<script>
export default {
   props: {
      sliderList: {
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
   <ul class="number-slider__container">
      <li
         class="number-slider__item"
         v-for="(tab, index) in sliderList"
         :key="tab.id"
      >
         <button
            class="number-slider__button"
            :class="{'number-slider__button--selected': selected === tab.id}"
            :title="tab.name"
            @click="onButtonClick(tab.id)"
         >{{ index + 1 }}</button>
      </li>
   </ul>
</template>

<style lang="scss">
.number-slider {
   &__container {
      display: flex;
      gap: 1em;
   }

   &__item {
      list-style: none;
   }

   &__button {
      cursor: pointer;
      width: var(--number-slider-size);
      height: var(--number-slider-size);
      border: 1px solid var(--number-slider-border-color);
      border-radius: 100%;
      color: var(--number-slider-color);
      background-color: transparent;

      &:hover {
         border-color: var(--number-slider-border-hover-color);
      }

      &--selected,
      &--selected:hover {
         background-color: var(--number-slider-active-background-color);
         color: var(--number-slider-active-color);
      }
   }
}
</style>