<template>
  <section class="emty-state">
    <img
      class="emty-state__iamge"
      src="@/assets/images/pokebola.svg"
      alt="Pokebola"
    />
    <h1 class="emty-state__title">Pokemon no encontrado</h1>
  </section>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.emty-state {
  &__image {
    width: 10rem;
    height: 10rem;
  }
  &__title {
    font-family: Roboto;
  }
}
</style>
