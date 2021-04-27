<template>
  <section class="browser">
    <img class="browser__logo" src="@/assets/images/logo.png" />

    <input
      v-model.trim="key"
      @keydown.enter="search"
      class="browser__input"
      type="text"
      placeholder="Find your pokemon"
    />
    <div class="browser__btn--group">
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
  justify-content: space-evenly;
  align-items: center;
  background: linear-gradient(to top, #fff, #6a86e0);
  height: 70vh;
  width: 100%;
  &__logo {
    width: 20rem;
    @media screen and (min-width: 768px) {
      width: 40rem;
    }
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
    margin: 0 1rem;
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
    &--group {
      display: flex;
    }
    @media screen and (min-width: 768px) {
      height: 4rem;
      width: 10rem;
    }
  }
}

.btn-recharge {
  background-color: #2563eb;
  &:hover {
    background-color: #2d8dd2;
  }
}
</style>
