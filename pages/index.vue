<template>
  <div class="container">
    <navbar />
    <browser @search-pokemon="getSearch" />
    <div class="card-wrapper">
      <div v-for="pokemon in pokemonList" :key="pokemon.id">
        <nuxt-link :to="`/CardDetail/${pokemon.id}`">
          <card :pokemon="pokemon"
        /></nuxt-link>
      </div>
      <emty-state v-if="pokemonList.length == 0" />
    </div>
  </div>
</template>

<script>
import env from '../api/pokeapi.js'
import axios from 'axios'
export default {
  data() {
    return {
      pokemonList: [],
      prueba: false,
    }
  },

  fetch() {
    this.getPokemons()
  },

  methods: {
    getSearch(value) {
      this.pokemonList = []
      if (value) {
        axios
          .get(`${env.endPoint}${value}`)
          .then((result) => {
            this.pokemonList.push(result.data)
          })
          .catch(() => {
            this.pokemonList = []
          })
      } else {
        this.getPokemons()
      }
    },

    async getPokemons() {
      let api = await axios.get(`${env.endPoint}`)
      let data = api.data.results
      data.forEach((res) => {
        axios
          .get(res.url)
          .then((response) => this.pokemonList.push(response.data))
      })
    },
  },
}
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.card-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 100%;
  @media screen and (min-width: 768px) {
    justify-content: space-around;
  }
}
</style>
