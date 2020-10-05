<template>
  <v-layout>
    <v-flex class="text-center">
      <img src="/ghibli.png" alt="Vuetify.js" class="mb-5" />

      <GhiblieMoviesList :movies="moviesList" />
    </v-flex>
  </v-layout>
</template>


<script>
import GhiblieMoviesList from "../../components/Ghibli/GhiblieMoviesList";
export default {
  async asyncData({ $axios }) {
    const moviesList = await $axios.$get(
      "https://ghibliapi.herokuapp.com/films"
    );
    return { moviesList };
  },
};
</script>

<style>
</style>