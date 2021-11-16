<template>
  <main class="mt-4">
    <div class="contain">
      <SelectGenre />
      <Card />
    </div>
  </main>
</template>

<script>
import Card from "./cards.vue";
import SelectGenre from "./selectGenre.vue";

export default {
  components: {
    Card,
    SelectGenre,
  },
};
</script>

<style lang="scss">
</style>