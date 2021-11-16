<template>
  <main class="mt-4">
    <div class="contain">
      <select class="mb-4" name="genre" id="">
        <option value="">Select Genre</option>
        <option value="">jazz</option>
        <option value="">rock</option>
        <option value="">pop</option>
      </select>

      <Card />
    </div>
  </main>
</template>

<script>
import Card from "./cards.vue";

export default {
  components: {
    Card,
  },
};
</script>

<style lang="scss">
</style>