<template>
  <v-container>
    <p v-if="!movie">Fetching Your Movie</p>
    <div v-else>
      <h1>{{ movie.title }} ({{ movie.release_date }})</h1>

      <v-subheader v-if="movie.producer === movie.director"
        >directed and produced by {{ movie.director }}</v-subheader
      >
      <v-subheader v-else
        >directed by {{ movie.director }}, produced by
        {{ movie.producer }}</v-subheader
      >
      <p style="max-width: 800px">{{ movie.description }}</p>
      <div id="details" style="margin-bottom: 40px">
        <dl
          v-for="movieDetail in movieDetails"
          :key="movieDetail.category"
          style="display: table-row"
        >
          <dt class="subs" v-if="movieDetail.icon">
            {{ movieDetail.category }} <v-icon>{{ movieDetail.icon }}</v-icon>
          </dt>
          <dt class="subs" v-else>
            {{ movieDetail.category }}
          </dt>
          <dd style="display: table-cell">{{ movieDetail.text }}</dd>
        </dl>
      </div>
      <v-btn elevation="2" fab color="secondary" @click="snackbar = true">
        <v-icon color="XD">mdi-play</v-icon></v-btn
      >
      <span style="margin-left: 1em">Play</span>
      <v-snackbar v-model="snackbar">
        {{ text }}

        <template v-slot:action="{ attrs }">
          <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
            Close
          </v-btn>
        </template>
      </v-snackbar>
    </div>
  </v-container>
</template>

<script>
export default {
  props: ["movie"],
  data: () => ({
    snackbar: false,
    movieDetails: [
      { category: "Genre", text: "Action, Animation" },
      { category: "Subtitles", text: "English, French", icon: "mdi-subtitles" },
      { category: "Audio 🎧", text: "Japanese, English" },
    ],
    text: "This is not an actual player 👏",
  }),
};
</script>

<style>
.subs {
  display: table-cell;
  padding: 0 20px 0 0;
  font-weight: 700;
  color: #c9a690;
}
</style>