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
   <ul class="point-slider__container">
      <li
         class="point-slider__item"
         v-for="tab in sliderList"
         :key="tab.id"
      >
         <button
            class="point-slider__button"
            :class="{'point-slider__button--selected': selected === tab.id}"
            :title="tab.name"
            @click="onButtonClick(tab.id)"
         />
      </li>
   </ul>
</template>

<style lang="scss">
.point-slider {
   &__container {
      display: flex;
      gap: 1em;
   }

   &__item {
      list-style: none;
   }

   &__button {
      width: var(--point-slider-size);
      height: var(--point-slider-size);
      border: none;
      border-radius: 100%;
      background-color: var(--point-slider-color);

      &:hover {
         background-color: var(--point-slider-hover-color);
      }

      &--selected,
      &--selected:hover {
         background-color: var(--point-slider-active-color);
      }
   }
}
</style>