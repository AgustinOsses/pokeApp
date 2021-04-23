<template>
  <section class="card">
    <img
      class="card__image"
      src="http://assets.stickpng.com/images/580b57fcd9996e24bc43c32a.png"
      alt=""
    />
    <div class="card__description-wrapper">
      <div>
        <h3 class="card__number">N°007</h3>
        <h2 class="card__name">Squirtle</h2>
      </div>
      <span class="card__badge">Agua</span>
    </div>
  </section>
</template>

<script>
export default {}
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
  &__image {
    overflow: hidden;
    padding: 1rem;
  }
  &__description-wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    margin-left: 2rem;
    width: 100%;
    height: 10rem;
  }
  &__number {
    color: gray;
    font-family: Roboto;
  }
  &__name {
    font-family: Roboto;
    color: black;
  }
  &__badge {
    font-family: Roboto;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 1rem 0;
    background-color: #4592c4;
    border-radius: 15px;
    width: 5rem;
    height: 1.5rem;
  }
}
</style>
