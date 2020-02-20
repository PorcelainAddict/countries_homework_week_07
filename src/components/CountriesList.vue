<template lang="html">
  <div>
    <select id="dropDownCountry" v-on:change="handleChange" v-model="selectedCountry">
      <option  v-for="(country, index) in countries" :country="country" :value="country" :key="index">{{country.name}}</option>
    </select>

  </div>
</template>

<script>
import ListItem from './ListItem.vue';
import {eventBus} from '../main.js'

export default {
  data(){
    return {
      "selectedCountry": {},
    }
  },
  name: 'countries-list',
  props: ['countries'],
  components: {
    "list-item": ListItem
  },
  methods: {
    handleChange() {
      eventBus.$emit('country-selected', this.selectedCountry);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
