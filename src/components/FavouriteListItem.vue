<template lang="html">
  <div id="favourite_countries">
    
    <li>
      <p>{{favouriteCountry.name}}</p>
      <img :src="favouriteCountry.flag" class="small-flag">
    </li>


  </div>
</template>

<script>
export default {
  name: 'favourite-countries',
  props: ['favouriteCountry']
}
</script>

<style lang="css" scoped>
.small-flag {
  height: 20px
}
</style>
