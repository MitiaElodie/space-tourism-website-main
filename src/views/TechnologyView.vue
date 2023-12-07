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
    <div class="technology-view__container">
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
          :initially-selected="selected.id"
          @click="onTechnologyClick"
        />
        <div class="technology-view__details-container">
          <h2 class="technology-view__terminology-label">The terminology...</h2>
          <h2 class="technology-view__name">{{ selected.name }}</h2>
          <p class="technology-view__description">{{ selected.description }}</p>
        </div>
      </div>
    </div>
  </PageBase>
</template>

<style lang="scss">
@use '@/assets/base.scss';
@use '@/assets/function.scss';

.technology-view {
  &__container {
    display: flex;
    flex-direction: column;
    text-align: center;
  }

  &__image-container {
    height: var(--technology-image-height);
    width: 100%;
  }

  &__image {
    height: 100%;
  }

  &__terminology-label,
  &__name {
    text-transform: uppercase;
    margin-bottom: 0.5em;
  }

  &__terminology-label,
  &__description {
    color: var(--color-secondary-text);
  }

  &__slider {
    justify-content: center;
  }

  &__information-container {
    display: flex;
    gap: 2em;
    flex-direction: column;
  }
}

.body__technology {
  background-image: url(function.generateBodyBackgroundUrl('technology','mobile'));
}

@media (min-width: base.$tablet-breakpoint) {
  .body__technology {
    background-image: url(function.generateBodyBackgroundUrl('technology','tablet'));
  }
}

@media (min-width: base.$laptop-breakpoint) {
  .technology-view {
    &__container {
      flex-direction: row;
      text-align: left;
    }

    &__image-container {
      order: 2;
    }

    &__slider {
      flex-direction: column;
    }

    &__information-container {
      flex-direction: row;
      align-items: center;
    }
  }

  .body__technology {
    background-image: url(function.generateBodyBackgroundUrl('technology','desktop'));
  }
}
</style>