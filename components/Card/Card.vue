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
        <span class="subtitle">Tipo</span>
      </div>
      <div class="card__weight-wrapper container">
        <span class="card__weight">{{ pokemon.weight }}Kg.</span>
        <span class="subtitle">Peso</span>
      </div>
      <div class="card__height-wrapper container">
        <span class="card__height">{{ pokemon.height }}m.</span>
        <span class="subtitle">Alura</span>
      </div>
    </div>
    <div class="card__abilities">
      <span class="card__abilities--title"><b> Habilidades</b></span>
      <div v-for="ability in pokemon.abilities" :key="ability.slot">
        <ul>
          <li class="card__abilities--item">{{ ability.ability.name }}</li>
        </ul>
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
  align-items: center;
  width: 20rem;
  height: 32rem;
  margin: 1rem 0;
  box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
  border-radius: 10px;

  &__image {
    background-image: linear-gradient(120deg, #d4fc79 0%, #96e6a1 100%);
    overflow: hidden;
    width: 100%;
    min-height: 15rem;
    height: 15rem;
    border-radius: 10px 10px 0 0;
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
    height: 4rem;
    margin: 1rem 0;
    box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
    padding: 0.5rem 0;
    background-color: #96e6a1;
    border-radius: 10px;
  }
  &__abilities {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    background-color: #d4fc79;
    flex-wrap: wrap;
    box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
    border-radius: 10px;
    width: 90%;
    padding: 0.5rem 0;
    &--title,
    &--item {
      list-style: none;
      font-size: 0.8rem;
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
  margin-top: 0.2rem;
  font-weight: 500;
  color: #000000;
  font-size: 1rem;
}
</style>
