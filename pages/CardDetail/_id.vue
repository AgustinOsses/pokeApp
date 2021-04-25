<template>
  <div>
    <pre>{{ pokemon }}</pre>
  </div>
</template>

<script>
import pokeApi from '../../api/pokeapi.js'
import axios from 'axios'

export default {
  data() {
    return {
      pokemon: null,
    }
  },

  async fetch() {
    axios.get(`${pokeApi.endPoint}${this.$route.params.id}`).then((result) => {
      this.pokemon = result.data
    })
  },
}
</script>

<style></style>
