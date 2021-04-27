<template>
  <section class="card">
    <img
      class="card__image"
      :src="pokemon.sprites.other.dream_world.front_default"
      :alt="pokemon.name"
    />
    <div class="card__description-wrapper">
      <h3 class="card__number">N°{{ pokemon.id }}</h3>
      <h2 class="card__name">{{ pokemon.name }}</h2>

      <div class="wrapper-info">
        <div class="card__experience">
          <span>{{ pokemon.base_experience }}</span>
          <h6>Experiencia base</h6>
          <span>{{ pokemon.weight }}</span>
          <h6>Peso</h6>
        </div>
        <div class="card__data">
          <span>{{ pokemon.height }}</span>
          <h6>Altura</h6>
          <span>{{ pokemon.weight }}</span>
          <h6>Peso</h6>
        </div>
      </div>
      <div class="container-ability">
        <div class="card__badge-wrapper">
          <div v-for="type in pokemon.types" :key="type.slot">
            <span class="card__badge"> {{ type.type.name }}</span>
          </div>
          <span>Tipo</span>
        </div>
        <div class="card__badge-wrapper">
          <div v-for="ability in pokemon.abilities" :key="ability.slot">
            <span class="card__badge"> {{ ability.ability.name }}</span>
          </div>
          <span>Habilidades</span>
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
  justify-content: space-between;
  margin: 1rem 0;
  border-radius: 10px;
  background-color: #fff;
  box-shadow: 1px 4px 10px -3px rgba(0, 0, 0, 0.75);
  width: 20rem;
  height: 40rem;
  margin: 1.5rem;
  &__image {
    background-image: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
    overflow: hidden;
    padding: 1rem;
    min-height: 15rem;
    height: 15rem;
  }
  &__description-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    // padding-left: 2rem;
  }
  &__experience {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  &__data {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 5rem;
    flex: 1 0 0;
  }
  &__number {
    color: gray;
    font-family: Roboto;
  }
  &__name {
    font-family: Roboto;
    color: black;
    &::first-letter {
      text-transform: uppercase;
    }
  }
  &__badge-wrapper {
    display: flex;
    flex-direction: column;
    flex-grow: grow;
    justify-content: flex-start;
    align-items: center;
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

.wrapper-info {
  display: flex;
  justify-content: space-around;
  width: 100%;
}

.container-ability {
  display: flex;
}

span {
  color: gray;
  font-size: 26px;
}
</style>
