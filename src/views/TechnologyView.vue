<script>
import PageBase from '@/components/PageBase.vue';
import NumberSlider from '@/components/NumberSlider.vue';

const technologyList = [
  {
    id: 'capsule',
    name: 'Space capsule',
    description: 'A space capsule is an often-crewed spacecraft that uses a blunt-body reentry capsule to reenter the Earth\'s atmosphere without wings. Our capsule is where you\'ll spend your time during the flight. It includes a space gym, cinema, and plenty of other activities to keep you entertained.',
    imageLandscape: '/img/technology/image-space-capsule-landscape.jpg',
    imagePortrait: '/img/technology/image-space-capsule-portrait.jpg',
  },
  {
    id: 'vehicle',
    name: 'Launch vehicle',
    description: 'A launch vehicle or carrier rocket is a rocket-propelled vehicle used to carry a payload from Earth\'s surface to space, usually to Earth orbit or beyond. Our WEB-X carrier rocket is the most powerful in operation. Standing 150 metres tall, it\'s quite an awe-inspiring sight on the launch pad!',
    imageLandscape: '/img/technology/image-launch-vehicle-landscape.jpg',
    imagePortrait: '/img/technology/image-launch-vehicle-portrait.jpg',
  },
  {
    id: 'spaceport',
    name: 'Spaceport',
    description: 'A spaceport or cosmodrome is a site for launching (or receiving) spacecraft, by analogy to the seaport for ships or airport for aircraft. Based in the famous Cape Canaveral, our spaceport is ideally situated to take advantage of the Earth’s rotation for launch.',
    imageLandscape: '/img/technology/image-spaceport-landscape.jpg',
    imagePortrait: '/img/technology/image-spaceport-portrait.jpg',
  },
]
export default {
  components: { PageBase, NumberSlider },

  data() {
    return {
      selected: technologyList[0],
      technologyList,
    }
  },

  methods: {
    onTechnologyClick(tabId) {
      this.selected = technologyList.find((item) => item.id === tabId)
    }
  }
}
</script>
<template>
  <PageBase
    order="03"
    title="Space launch 101"
  >
  <div class="technology-view__image-container">
    <picture>
      <source class="technology-view__image" :srcset="selected.imagePortrait" media="(min-width: 760px)" />
      <img class="technology-view__image" :src="selected.imageLandscape" :alt="`Image of ${ selected.name }`" />
    </picture>
  </div>
    <div class="technology-view__information-container">
      <NumberSlider
        class="technology-view__slider"
        :slider-list="technologyList"
        :initially-selected="selected"
        @click="onTechnologyClick"
      />
      <div class="technology-view__details-container">
        <h2 class="technology-view__terminology-label">The terminology...</h2>
        <h2 class="technology-view__name">{{ selected.name }}</h2>
        <p class="technology-view__description">{{ selected.description }}</p>
      </div>
    </div>
  </PageBase>
</template>

<style lang="scss">
.technology-view {
  &__image-container {
    height: var(--technology-image-height);
    width: 100%;
  }

  &__image {
    height: 100%;
  }
}
</style>