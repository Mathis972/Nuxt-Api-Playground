<template>
  <p v-if="!movies">Fetching Movies</p>

  <div v-else>
    <h1>Movies</h1>
    <ul>
      <li v-for="movie of movies" :key="movie.id">{{ movie.title }}</li>
    </ul>
    <button @click="$fetch">Refresh</button>
  </div>
</template>

<script>
export default {
  props: ["movies"],
};
</script>

<style>
</style>