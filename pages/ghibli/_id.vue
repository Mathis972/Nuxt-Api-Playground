<template>
  <GhibliMoviePage :movie="movie" />
</template>

<script>
import GhibliMoviePage from "../../components/Ghibli/GhibliMoviePage.vue";
export default {
  async asyncData({ params, $axios }) {
    const movie = await $axios.$get(
      "https://ghibliapi.herokuapp.com/films/" + params.id
    );
    return { movie };
  },
};
</script>

<style>
</style>