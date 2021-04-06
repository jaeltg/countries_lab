<template lang="html">
  <div id="favourite_countries">
    
    <li >{{favouriteCountry.name}}</li>


  </div>
</template>

<script>
export default {
  name: 'favourite-countries',
  props: ['favouriteCountry']
}
</script>

<style lang="css" scoped>
</style>
