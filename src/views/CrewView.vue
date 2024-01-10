<script>
import PageBase from '@/components/PageBase.vue';
import PointSlider from '@/components/PointSlider.vue';

const crewList = [
  {
    id: 'commander',
    name: 'Douglas Hurley',
    role: 'Commander',
    biography: 'Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.',
    image: '/img/crew/image-douglas-hurley.png',
  },
  {
    id: 'engineer',
    name: 'Anousheh Ansari',
    role: 'Flight Engineer',
    biography: 'Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.',
    image: '/img/crew/image-anousheh-ansari.png',
  },
  {
    id: 'pilot',
    name: 'Victor Glover',
    role: 'Pilot',
    biography: 'Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.',
    image: '/img/crew/image-victor-glover.png',
  },
  {
    id: 'specialist',
    name: 'Mark Shuttleworth',
    role: 'Mission Specialist',
    biography: 'Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.',
    image: '/img/crew/image-mark-shuttleworth.png',
  },
]

export default {
  components: { PageBase, PointSlider },

  data() {
    return {
      crewList,
      selected: crewList[0],
    }
  },

  methods: {
    onCrewClick(tabId) {
      this.selected = crewList.find((item) => item.id === tabId)
    }
  },
}
</script>
<template>
  <PageBase
    order="02"
    title="Meet our crew"
    class="crew-view"
  >
    <div class="crew-view__container">
      <div class="crew-view__image-container">
        <img
          class="crew-view__image"
          :src="selected.image"
          :alt="`Portrait of ${ selected.name }`"
        >
      </div>
      <div class="crew-view__information-container">
        <PointSlider
          class="crew-view__slider"
          :slider-list="crewList"
          :initially-selected="selected.id"
          @click="onCrewClick"
        />
        <div class="crew-view__details">
          <span class="crew-view__role">{{ selected.role }}</span>
          <h2 class="crew-view__name">{{ selected.name }}</h2>
          <p class="crew-view__biography">{{ selected.biography }}</p>
        </div>
      </div>
    </div>
  </PageBase>
</template>

<style lang="scss">
@use '@/assets/base.scss';
@use '@/assets/function.scss';

.crew-view {
  --role-size: 16px;
  --name-size: 24px;

  &__container {
    display: flex;
    flex-direction: column;
    gap: 30px;

    text-align: center;
  }

  &__image-container {
    height: var(--crew-image-size);
    border-bottom: 0.25px solid var(--crew-separator-color);
  }

  &__image {
    height: 100%;
  }

  &__slider {
    justify-content: center;
  }

  &__information-container {
    display: flex;
    flex-direction: column;
    gap: 2em;
  }

  &__role,
  &__name {
    text-transform: uppercase;
  }

  &__role {
    display: block;
    color: var(--crew-role-color);
    font-size: var(--role-size);
    margin-bottom: 16px;
  }

  &__name {
    font-size: var(--name-size);
    font-weight: 400;
    margin-bottom: 16px;
  }

  &__biography {
    color: var(--color-secondary-text);
    font-size: var(--body-size);
    line-height: var(--body-line-height);
  }
}

@media (min-width: base.$tablet-breakpoint) {
  .crew-view {
    --role-size: 24px;
    --name-size: 40px;

    &__information-container,
    &__details {
      order: 1;
    }

    &__details {
      max-width: var(--crew-information-max-width);
    }

    &__image-container,
    &__slider {
      order: 2;
    }
  }
}

@media (min-width: base.$laptop-breakpoint) {
  .crew-view {
    --role-size: 32px;
    --name-size: 56px;

    &__container {
      flex-direction: row;
      justify-content: space-around;
      text-align: left;
    }

    &__information-container {
      align-items: start;
      justify-content: space-around;
    }
  }
}
</style>
