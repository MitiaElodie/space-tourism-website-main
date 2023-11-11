<script>
export default {
   props: {
      order: {
         type: String,
         required: true,
      },

      title: {
         type: String,
         required: true,
      }
   }
}
</script>
<template>
   <div class="page-base">
      <h1 class="page-base__title-container">
         <span class="page-base__order">{{ order }}</span>
         <span class="page-base__title">{{ title }}</span>
      </h1>
      <slot />
   </div>
</template>