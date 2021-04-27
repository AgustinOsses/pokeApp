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
  height: 7rem;
  background-color: #db092b;
  @media screen and (min-width: 768px) {
    justify-content: flex-start;
    height: 5rem;
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
