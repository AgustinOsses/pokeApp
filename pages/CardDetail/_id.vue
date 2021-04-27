<template>
  <div class="pokemon-detail">
    <div>
      <!-- <img :src="pokemon.sprites.other.dream_world.front_default" alt="" /> -->
    </div>
    <pre>{{ pokemon.name }}</pre>
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
    await axios
      .get(`${pokeApi.endPoint}${this.$route.params.id}`)
      .then((result) => {
        this.pokemon = result.data
      })
    return this.pokemon
  },
}
</script>

<style></style>
