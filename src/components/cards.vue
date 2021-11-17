<template>
  <div>
    <SelectGenre @musicGenre="genre" />

    <SelectAuthor @musicAuthor="author" />

    <div v-if="loader">
      <div
        class="row row-cols-6 justify-content-center g-4"
        v-if="selectGen.length > 0"
      >
        <div class="col" v-for="card in selectGen" :key="card.title">
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
      <h2 class="text-danger mt-5 text-center" v-else>
        No songs with this filter bro!
      </h2>
    </div>
    <div v-else>
      <h1 class="text-light text-center mt-5">Loading your songs..</h1>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SelectGenre from "./selectGenre.vue";
import SelectAuthor from "./selectAuthor.vue";

export default {
  data() {
    return {
      cards: [],
      loader: false,
      musicGen: "all",
      musicAuthor: "all",
    };
  },

  components: {
    SelectGenre,
    SelectAuthor,
  },

  mounted() {
    this.genAlbums();
  },

  methods: {
    genAlbums() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((resp) => {
          this.loader = resp.data.success;
          this.cards = resp.data.response;
        });
    },

    genre(select) {
      this.musicGen = select;
    },

    author(select) {
      this.musicAuthor = select;
    },
  },

  computed: {
    selectGen() {
      if (this.musicGen === "all" && this.musicAuthor === "all") {
        return this.cards;
      } else if (this.musicGen !== "all" && this.musicAuthor !== "all") {
        return this.cards.filter(
          (card) =>
            card.genre === this.musicGen && card.author === this.musicAuthor
        );
      }
      return this.cards.filter(
        (card) =>
          card.genre === this.musicGen || card.author === this.musicAuthor
      );
    },
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