<template>
  <v-layout>
    <v-flex class="text-center">
      <img src="/ghibli.png" alt="Vuetify.js" class="mb-5" />
      <blockquote class="blockquote">
        &#8220;PD.&#8221;
        <footer>
          <small>
            <em>&mdash;John Johnson</em>
          </small>
        </footer>
      </blockquote>
      <GhiblieMoviesList :movies="moviesList" />
    </v-flex>
  </v-layout>
</template>


<script>
import GhiblieMoviesList from "../components/Ghibli/GhiblieMoviesList";
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