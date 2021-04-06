<template>
  <div id="app">

    <label for="country_select">Select a Country:</label>
    <select @click="fetchCountries()" @change="selectNeighbouringCountries(); convertCodesToCountries();"  id="country_select" v-model="selectedCountry">
      <option disabled value="">Select a country</option>
      <option  v-for="country in countries" :key="country.alpha3code" :value="country" :v-model="selectedCountry"> {{country.name}}</option>
    </select>

    <country-detail v-if="selectedCountry !== null" :selectedCountry="selectedCountry" :neighbouringCountries="neighbouringCountries"></country-detail>

    <button @click="favouriteCountry" :v-model="favouriteCountries">Add Country to favourites</button>
    <h2>Favourite Countries</h2>
    <ul>
      <favourite-countries v-for="favouriteCountry in favouriteCountries" :key="favouriteCountry.alpha3code" :favouriteCountry="favouriteCountry"></favourite-countries>
    </ul>

</div>

</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
import FavouriteListItem from './components/FavouriteListItem.vue';

export default {
  name: 'App',
  data() {
    return {
      countries: [],
      selectedCountry: null,
      favouriteCountries: [],
      neighbouringCountriesIds: [],
      neighbouringCountries: []

    }
  },
  components: {
    'country-detail': CountryDetail,
    'favourite-countries': FavouriteListItem
  },
    mounted(){
      this.fetchCountries()
     
    },
    methods: {
      fetchCountries: function() {
        fetch("https://restcountries.eu/rest/v2/all")
        .then((response) => response.json())
        .then((data) => this.countries = data)
        
      },
      favouriteCountry: function() {
        if (this.favouriteCountries.includes(this.selectedCountry)) {
          return
        } else {
        this.favouriteCountries.push(this.selectedCountry) 
        }
      },
        selectNeighbouringCountries: function() {
        this.neighbouringCountriesIds = this.selectedCountry.borders 
      },
        convertCodesToCountries: function() {
          this.neighbouringCountries = []
          for (const id of this.neighbouringCountriesIds){ 
            for (const country of this.countries){
              if(id === country.alpha3Code){
                this.neighbouringCountries.push(country)
              }
            }
          }
        }    
      },
}
</script>

<style>






</style>
