<template>
  <main>
    <div class="card card_color" style="width: 18rem">
      <img src="" class="card-img-top" alt="..." />
      <div class="card-body">
        <h5 class="card-title text-light text-center">Card title</h5>
        <p class="card-text text-light text-center">
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </p>
      </div>
    </div>
  </main>
</template>

<script>
export default {};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.card_color {
  background-color: $card_color;
}
</style>