<template>
  <p v-if="!movies">Fetching Movies</p>

  <div v-else>
    <h1>Movies</h1>
    <ul>
      <li v-for="movie of movies" :key="movie.id">
        <nuxt-link :to="{ path: '/ghibli/' + movie.id }">{{
          movie.title
        }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["movies"],
};
</script>

<style>
</style>