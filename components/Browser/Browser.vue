<template>
  <section class="browser">
    <img class="browser__logo" src="@/assets/images/pokedex-logo.png" />

    <input
      v-model.trim="key"
      @keydown.enter="search"
      class="browser__input"
      type="text"
      placeholder="Find your pokemon"
    />
    <div class="browser__btn-group">
      <button class="browser__btn btn-recharge" @click="recharge">
        Recharge
      </button>
      <button class="browser__btn" @click="search">Consult</button>
    </div>
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
    recharge() {
      this.key = ''
      this.$emit('search-pokemon', this.key)
    },
  },
}
</script>

<style lang="scss" scoped>
.browser {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(to top, #fff, #6a86e0);
  height: 70vh;
  width: 100%;
  &__logo {
    width: 70%;
    max-height: 20rem;
    @media screen and (min-width: 768px) {
      width: 40rem;
    }
  }
  &__input {
    width: 70%;
    min-height: 3rem;
    padding-left: 1rem;
    border-radius: 10px;
    outline: none;
    border: none;
    margin: 3rem 0;
    @media screen and (min-width: 768px) {
      width: 50%;
    }
  }
  &__btn-group {
    display: flex;
    justify-content: space-between;
    width: 75%;
    @media screen and (min-width: 768px) {
      width: 50%;
      justify-content: center;
    }
  }
  &__btn {
    width: 8rem;
    height: 3rem;
    border-radius: 10px;
    background-color: #fd0004;
    color: white;
    font-size: 1.2rem;
    outline: none;
    border: none;
    box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
    cursor: pointer;
    &:hover {
      background-color: #ff3336;
    }

    @media screen and (min-width: 768px) {
      height: 3rem;
      width: 10rem;
    }
  }
}

.btn-recharge {
  background-color: #2563eb;
  margin-right: 1rem;
  &:hover {
    background-color: #2d8dd2;
  }
}
</style>
