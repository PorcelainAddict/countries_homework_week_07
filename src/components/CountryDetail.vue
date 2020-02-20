<template lang="html">
  <div v-if='country'>
    <h3>{{country.name}}</h3>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <p v-for="(language, index) in country.languages">Languages: {{language.name}}</p>
    <img id="flag" :src=country.flag>
  </div>
</template>


<script>
import {eventBus} from '../main.js'

export default {
  name: 'CountryDetail',
  data() {
    return {
      country: null,
    }
  },
  mounted() {
    eventBus.$on("country-selected", (country) => this.country = country)
  }
}
</script>

<style lang="css" scoped>
div {
  position: fixed;
  top: 20px;
  right: 20px;
}

#flag {
  height: 400px;
  width: 600px;
  border: 2px;
}
</style>
