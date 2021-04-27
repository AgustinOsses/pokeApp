<template>
  <section class="emty-state">
    <div class="emty-state__wrapper">
      <img
        class="emty-state__img"
        src="@/assets/images/psyduck530.png"
        alt=""
      />
    </div>
    <h2>{{ title }} not found</h2>
  </section>
</template>

<script>
export default {
  props: {
    title: {
      tyoe: String,
      default: 'Pokémon',
    },
  },
}
</script>

<style lang="scss" scoped>
.emty-state {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  &__wrapper {
    width: 20rem;
  }
  &__img {
    width: 100%;
  }
}
</style>
