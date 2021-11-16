<template>
  <select class="mb-4" name="genre" id="">
    <option value="">Select Genre</option>
    <option
      v-for="genre in genres"
      :key="genre.author"
      value=""
      v-show="!genres.includes(genre.genre)"
    >
      {{ genre.genre }}
    </option>
  </select>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      genres: [],
    };
  },

  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.genres = resp.data.response;
        console.log(this.genres);
      });
  },
};
</script>

<style lang="scss">
</style>