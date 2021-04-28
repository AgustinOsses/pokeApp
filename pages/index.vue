<template>
  <div class="container">
    <browser @search-pokemon="getSearch" :pokemonArray="pokemonList" />
    <div class="card-wrapper">
      <div v-for="pokemon in pokemonList" :key="pokemon.id">
        <card :pokemon="pokemon" />
      </div>
      <emty-state class="emty-state" v-if="pokemonList.length == 0" />
    </div>
    <button
      v-if="pokemonList.length > 1"
      class="btn-show-more"
      @click="showMore"
    >
      Show more
    </button>
  </div>
</template>

<script>
import pokeApi from '../api/pokeapi.js'
import axios from 'axios'
export default {
  data() {
    return {
      pokemonList: [],
    }
  },

  fetch() {
    this.getPokemons()
  },

  methods: {
    showMore() {
      axios
        .get(`${pokeApi.endPoint}?limit=10&offset=${this.pokemonList.length}`)
        .then((resolve) => {
          let data = resolve.data.results
          data.forEach((res) => {
            axios
              .get(res.url)
              .then((response) => this.pokemonList.push(response.data))
          })
        })
    },

    getSearch(value) {
      this.pokemonList = []
      if (value) {
        axios
          .get(`${pokeApi.endPoint}${value}`)
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
      let api = await axios.get(`${pokeApi.endPoint}`)
      let data = api.data.results
      data.forEach((res) => {
        axios.get(res.url).then((response) => {
          this.pokemonList.push(response.data)
        })
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
  background-color: #fefefe;
  width: 100%;
  margin-top: 2rem;
  @media screen and (min-width: 768px) {
    justify-content: space-around;
  }
}
.card {
  text-decoration: none;
}

.emty-state {
  margin: 5rem 0;
}

.btn-show-more {
  width: 8rem;
  height: 3rem;
  border-radius: 10px;
  background-color: #2563eb;
  color: white;
  margin: 2rem 0;
  font-size: 1.2rem;
  outline: none;
  border: none;
  box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
  cursor: pointer;
  &:hover {
    background-color: #2d8dd2;
  }
}
</style>
