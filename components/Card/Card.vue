<template>
  <section class="card">
    <img
      class="card__image"
      :src="pokemon.sprites.other.dream_world.front_default"
      :alt="pokemon.name"
    />

    <h1 class="card__title">
      {{ pokemon.name.toUpperCase() }}
    </h1>
    <p class="card__experience">
      Exp. base <b>{{ pokemon.base_experience }} </b>
    </p>
    <div class="card__wrapper-details">
      <div class="container">
        <div
          class="card__type-wrapper"
          v-for="type in pokemon.types"
          :key="type.slot"
        >
          <span class="card__type">{{ type.type.name }}</span>
        </div>
        <span class="subtitle">Type</span>
      </div>
      <div class="card__weight-wrapper container">
        <span class="card__weight">{{ pokemon.weight }}</span>
        <span class="subtitle">Weight</span>
      </div>
      <div class="card__height-wrapper container">
        <span class="card__height">{{ pokemon.height }}</span>
        <span class="subtitle">Height</span>
      </div>
    </div>
    <div class="card__abilities">
      <span class="card__abilities--title">Abilities</span>
      <div class="card__abilities--wrapper">
        <div v-for="ability in pokemon.abilities" :key="ability.slot">
          <ul>
            <li class="card__abilities--item">{{ ability.ability.name }}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import numeral from 'numeral'

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
  align-items: center;
  width: 20rem;
  min-height: 33rem;
  height: 34rem;
  margin: 1rem 0;
  box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
  border-radius: 10px;
  background-color: #f3f3f3;
  &__image {
    background-image: linear-gradient(120deg, #d4fc79 0%, #96e6a1 100%);
    width: 100%;
    min-height: 15rem;
    height: 15rem;
    border-radius: 10px 10px 0 0;
    overflow: hidden;
  }
  &__title {
    display: flex;
    justify-content: center;
    width: 70%;
    margin: 1rem 0;
    padding-bottom: 1rem;
    border-bottom: 5px solid #9ce89d;
  }
  &__experience {
    color: gray;
  }
  &__wrapper-details {
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 90%;
    min-height: 4rem;
    margin: 1rem 0;
    box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
    padding: 0.5rem 0;
    background-color: #96e6a1;
    border-radius: 10px;
  }
  &__weight {
    font-size: 1.5rem;
    font-weight: 800;
  }
  &__type {
    font-size: 1.1rem;
    font-weight: 800;
  }
  &__height {
    font-size: 1.5rem;
    font-weight: 800;
  }
  &__abilities {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    border-radius: 10px;
    width: 80%;
    height: auto;
    padding: 1rem;
    &--wrapper {
      display: flex;
      flex-wrap: wrap;
      width: 100%;
    }
    &--title {
      width: 3rem;
      font-weight: bold;
      font-size: 0.8rem;
      margin-right: 0.3rem;
    }
    &--item {
      background-color: #96e6a1;
      border-radius: 5px;
      margin: 0.2rem 0.3rem 0.2rem 0;
      list-style: none;
      font-size: 0.8rem;
      padding: 0.1rem 0.5rem;
      box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
    }
  }
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
  text-align: left;
  height: 3rem;
}
.subtitle {
  letter-spacing: 0.1rem;
  margin-top: 0.2rem;

  // color: #7e7d82;
  color: #000;
  font-size: 0.8rem;
}
</style>
