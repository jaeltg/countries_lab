<template lang="html">
  <div id="neighbouring_countries">
  
    <ul id="neighbouring_countries">
      <li>
       <p>{{neighbouringCountry.name}}</p>
       <img :src="neighbouringCountry.flag" class="med-flag">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'neighbouring-countries',
  props: ['neighbouringCountry']
}
</script>

<style lang="css" scoped>

.med-flag {
  height: 40px
}
</style>
