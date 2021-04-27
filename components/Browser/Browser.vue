<template>
  <section class="browser">
    <h1 class="browser__title">Pokedex</h1>
    <input
      v-model.trim="key"
      @keydown.enter="search"
      class="browser__input"
      type="text"
      placeholder="Find your pokemon"
    />
    <div class="browser__btn--group">
      <button class="browser__btn" @click="search">Consult</button>
      <button class="browser__btn btn-recharge" @click="recharge">
        Recharge
      </button>
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
  // background: linear-gradient(to right, #76b852, #8dc26f);
  // background: linear-gradient(
  //   to right,
  //   #33b1ff,
  //   hsl(239, 47%, 80%)
  // );
  // background: linear-gradient(to right, #e53935, #e35d5b);
  background: linear-gradient(to right, #757f9a, #d7dde8);
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
    margin: 0 1rem;
    background-color: #d5082d;
    color: white;
    font-size: 1.2rem;
    outline: none;
    border: none;
    box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
    cursor: pointer;
    &:hover {
      background-color: #d34761;
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
  background-color: #348ac7;
  &:hover {
    background-color: #6bafe0;
  }
}
</style>
