<template>
  <select
    v-model="select"
    class="mb-4"
    name="author"
    id=""
    @change="$emit('musicAuthor', select)"
  >
    <option value="all">Select Author</option>
    <option v-for="artist in artists" :key="artist.author" :value="artist">
      {{ artist }}
    </option>
  </select>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      artists: [],
      select: "all",
    };
  },

  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        resp.data.response.forEach((album) => {
          if (!this.artists.includes(album.author)) {
            this.artists.push(album.author);
          }
        });
      });
  },
};
</script>

<style lang="scss">
</style>