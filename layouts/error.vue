<template>
  <div class="error">
    <emty-state title="Page" />
    <nuxt-link to="/"> Go home </nuxt-link>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.error {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 90vh;
}
</style>
