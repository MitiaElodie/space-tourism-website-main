<script>
import PageBase from '@/components/PageBase.vue';
import TextTabs from '@/components/TextTabs.vue';
import DestinationDetails from '@/components/DestinationDetails.vue';

const destinationList = [
  {
    id: 'moon',
    name: 'Moon',
    description: 'See our planet as you’ve never seen it before. A perfect relaxing trip away to help regain perspective and come back refreshed. While you’re there, take in some history by visiting the Luna 2 and Apollo 11 landing sites.',
    distance: '384,400',
    travelTime: '3 days',
    image: '/img/destination/image-moon.png',
  },
  {
    id: 'mars',
    name: 'Mars',
    description: 'Don’t forget to pack your hiking boots. You’ll need them to tackle Olympus Mons, the tallest planetary mountain in our solar system. It’s two and a half times the size of Everest!',
    distance: '225 mil.',
    travelTime: '9 months',
    image: '/img/destination/image-mars.png',
  },
  {
    id: 'europa',
    name: 'Europa',
    description: 'The smallest of the four Galilean moons orbiting Jupiter, Europa is a winter lover’s dream. With an icy surface, it’s perfect for a bit of ice skating, curling, hockey, or simple relaxation in your snug wintery cabin.',
    distance: '628 mil.',
    travelTime: '3 years',
    image: '/img/destination/image-europa.png',
  },
  {
    id: 'titan',
    name: 'Titan',
    description: 'The only moon known to have a dense atmosphere other than Earth, Titan is a home away from home (just a few hundred degrees colder!). As a bonus, you get striking views of the Rings of Saturn.',
    distance: '1.6 bil.',
    travelTime: '7 years',
    image: '/img/destination/image-titan.png',
  },
]

export default {
  components: { PageBase, TextTabs, DestinationDetails },

  data() {
    return {
      selected: destinationList[0],
      destinationList,
    }
  },

  methods: {
    onDestinationClick(tabId) {
      this.selected = destinationList.find((item) => item.id === tabId)
    }
  }
}
</script>
<template>
  <PageBase
    order="01"
    title="Pick your destination"
  >
    <div
      class="destination-view__container"
    >
      <div class="destination-view__image-container">
        <img :src="selected.image" :alt="`Image of ${ selected.name }`"/>
      </div>
      <div class="destination-view__information-container">
        <TextTabs
          class="destination-view__tabs"
          :tab-list="destinationList"
          :initially-selected="selected.id"
          @click="onDestinationClick"
        />
        <DestinationDetails
          :destination="selected"
        />
      </div>
    </div>
  </PageBase>
</template>

<style lang="scss">
@use '@/assets/base.scss';

.destination-view {
  &__image-container {
    display: flex;
    justify-content: center;
    height: var(--destination-image-size);
    margin-bottom: 2em;
  }

  &__tabs {
    justify-content: center;
  }
}

@media (min-width: base.$laptop-breakpoint) {
  .destination-view {
    &__container {
      display: flex;
      gap: 5em;
    }

    &__tabs {
      justify-content: start;
    }
  }
}
</style>
