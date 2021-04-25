<template>
  <section class="browser">
    <h1 class="browser__title">Pokedex</h1>
    <input
      v-model.trim="key"
      @keydown.enter="search"
      class="browser__input"
      type="text"
      placeholder="Busca tu pokémon"
    />
    <button @click="search" class="browser__btn">Consultar</button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      key: '',
    }
  },
  methods: {
    search() {
      let keyLower = this.key.toLowerCase()
      this.$emit('search-pokemon', keyLower)
    },
  },
}
</script>

<style lang="scss" scoped>
.browser {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  background-color: #798897;
  height: 70vh;
  width: 100%;
  &__title {
    font-family: Roboto;
    color: white;
    font-size: 4rem;
  }
  &__input {
    width: 70%;
    height: 4rem;
    padding-left: 1rem;
    font-size: 1rem;
    border-radius: 10px;
    outline: none;
    border: none;
  }
  &__btn {
    width: 8rem;
    height: 3rem;
    border-radius: 10px;
    background-color: #d5082d;
    color: white;
    font-size: 1.2rem;
    outline: none;
    border: none;
    @media screen and (min-width: 768px) {
      height: 4rem;
      width: 10rem;
    }
  }
}
</style>
