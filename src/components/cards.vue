<template>
  <div class="row row-cols-2 row-cols-sm-4 row-cols-lg-6">
    <div class="col" v-for="card in cards" :key="card.title">
      <div class="card_color" style="width: 18rem">
        <img
          :src="card.poster"
          class="card-img-top"
          :alt="card.title"
          width="90%"
        />
        <div class="card-body">
          <h5 class="card-title text-light text-center">{{ card.title }}</h5>
          <p class="card-text text-light text-center">{{ card.author }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      cards: [],
    };
  },
  components: {},

  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.cards = resp.data.response;
        console.log(resp.data.response);
      });
  },
};
</script>

<style lang="scss">
@import "../assets/scss/variables.scss";

.card_color {
  background-color: $card_color;
}
</style>