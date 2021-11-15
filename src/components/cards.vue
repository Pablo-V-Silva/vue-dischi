<template>
  <div class="row row-cols-6 justify-content-center g-4" v-if="loader">
    <div class="col" v-for="card in cards" :key="card.title">
      <div class="card_color">
        <div class="imgcontain">
          <img :src="card.poster" class="card-img-top" :alt="card.title" />
        </div>
        <div class="card-body">
          <h5 class="card-title text-light text-center">
            {{ card.title.toUpperCase() }}
          </h5>
          <div class="card-text text-secondary text-center">
            {{ card.author }}
          </div>
          <div class="card-text text-secondary text-center">
            {{ card.year }}
          </div>
        </div>
      </div>
    </div>
  </div>

  <div v-else>
    <h1 class="text-light text-center mt-5">Loading your songs..</h1>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      cards: [],
      loader: false,
    };
  },
  components: {},

  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.loader = resp.data.success;
        this.cards = resp.data.response;
        console.log(resp.data.success);
      });
  },
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.card_color {
  background-color: #2e3a46;
  min-height: 100%;

  .imgcontain {
    width: 70%;
    margin: auto;
    padding-top: 1rem;
  }
}
</style>