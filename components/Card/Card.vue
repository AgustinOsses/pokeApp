<template>
  <section class="card">
    <img
      class="card__image"
      :src="pokemon.sprites.other.dream_world.front_default"
      alt=""
    />
    <div class="card__description-wrapper">
      <div>
        <h3 class="card__number">N°{{ pokemon.id }}</h3>
        <h2 class="card__name">{{ pokemon.name }}</h2>
      </div>
      <div class="card__badge-wrapper">
        <div v-for="type in pokemon.types" :key="type.slot">
          <span class="card__badge">{{ type.type.name }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    pokemon: {
      type: Object,
      default: () => {},
    },
  },
}
</script>

<style lang="scss" scoped>
.card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 2rem 0;
  border-radius: 10px;
  box-shadow: 2px 2px 10px black;
  width: 16rem;
  height: 25rem;
  margin: 2rem;
  &__image {
    overflow: hidden;
    padding: 1rem;
    height: 15rem;
  }
  &__description-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    width: 100%;
    height: 10rem;
    padding-left: 2rem;
  }
  &__number {
    color: gray;
    font-family: Roboto;
  }
  &__name {
    font-family: Roboto;
    color: black;
  }
  &__badge-wrapper {
    display: flex;
    width: 100%;
  }
  &__badge {
    font-family: Roboto;
    font-size: 0.8rem;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 1rem 0.5rem 1rem 0;
    background-color: #4592c4;
    border-radius: 15px;
    width: 5rem;
    height: 1.2rem;
  }
}
</style>
