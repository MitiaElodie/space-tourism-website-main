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
  }
}
</script>
<template>
  <PageBase
    order="02"
    title="Meet our crew"
  >
    <div class="crew-view__container">
      <div class="crew-view__image-container">
        <img :src="selected.image" :alt="`Portrait of ${ selected.name }`">
      </div>
      <div class="crew-view__information-container">
        <PointSlider
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
