<script>
import PageBase from '@/components/PageBase.vue';
import PointSlider from '@/components/PointSlider.vue';

const crewList = [
  {
    id: 'commander',
    name: 'Douglas Hurley',
    role: 'Commander',
    biography: 'Douglas Gerald Hurley is an American engineer, former Marine Corps pilot and former NASA astronaut. He launched into space for the third time as commander of Crew Dragon Demo-2.',
  },
  {
    id: 'engineer',
    name: 'Anousheh Ansari',
    role: 'Flight Engineer',
    biography: 'Anousheh Ansari is an Iranian American engineer and co-founder of Prodea Systems. Ansari was the fourth self-funded space tourist, the first self-funded woman to fly to the ISS, and the first Iranian in space.',
  },
  {
    id: 'pilot',
    name: 'Victor Glover',
    role: 'Pilot',
    biography: 'Pilot on the first operational flight of the SpaceX Crew Dragon to the International Space Station. Glover is a commander in the U.S. Navy where he pilots an F/A-18.He was a crew member of Expedition 64, and served as a station systems flight engineer.',
  },
  {
    id: 'specialist',
    name: 'Mark Shuttleworth',
    role: 'Mission Specialist',
    biography: 'Mark Richard Shuttleworth is the founder and CEO of Canonical, the company behind the Linux-based Ubuntu operating system. Shuttleworth became the first South African to travel to space as a space tourist.',
  },
]

export default {
  components: { PageBase, PointSlider },
  data() {
    return { crewList }
  },
}
</script>
<template>
  <PageBase
    order="02"
    title="Meet our crew"
  >
    <PointSlider
      :slider-list="crewList"
    />
  </PageBase>
</template>
