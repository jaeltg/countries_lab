<template lang="html">
  <div id="selected_country">
  <h2> {{ selectedCountry.name }} </h2>
  <div id="country-deets">
  <div> 
    <p> Population: {{ selectedCountry.population }} </p>
    <img class="lrg-flag" :src="selectedCountry.flag"/>
  </div>  
  <div>
    <h3>Neighbouring Countries</h3>
    <neighbouring-countries v-for="neighbouringCountry in neighbouringCountries" :key="neighbouringCountry.alpha3code" :neighbouringCountry="neighbouringCountry">
    </neighbouring-countries>
  </div>
</div>
</div>
</template>

<script>
import NeighbourCountry from './NeighbourCountry.vue';
export default {
  name: 'country-detail',
  props: ['selectedCountry', 'neighbouringCountries'], 
  components: {
    'neighbouring-countries': NeighbourCountry
  }

  // methods: {
  //   selectNeighbouringCountries: function() {
  //       this.neighbouringCountries = this.selectedCountry.borders 
  //     }
  // }
}
</script>

<style lang="css" scoped>

.lrg-flag {
  height: 100px
}

#country-deets {
  display: flex;
  flex-flow: row wrap;
  gap: 40px;

}

</style>
