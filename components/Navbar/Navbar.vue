<template>
  <nav class="navbar">
    <nuxt-link to="/">
      <img
        class="navbar__image"
        src="@/assets/images/pokemon.png"
        alt="logo-pokemon"
      />
    </nuxt-link>
  </nav>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.navbar {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 5rem;
  background-color: #fd0004;
  @media screen and (min-width: 768px) {
    justify-content: flex-start;
  }
  &__image {
    width: 10rem;
    @media screen and (min-width: 768px) {
      justify-content: flex-start;
      margin-left: 2rem;
    }
  }
}
</style>
