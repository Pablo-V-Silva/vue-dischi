<template>
  <select
    v-model="select"
    class="mb-4"
    name="genre"
    id=""
    @change="$emit('musicGenre', select)"
  >
    <option value="all">Select Genre</option>
    <option v-for="genre in genres" :key="genre.author" :value="genre">
      {{ genre }}
    </option>
  </select>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      genres: [],
      select: "all",
    };
  },

  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        resp.data.response.forEach((album) => {
          if (!this.genres.includes(album.genre)) {
            this.genres.push(album.genre);
          }
        });
      });
  },
};
</script>

<style lang="scss">
</style>