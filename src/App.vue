<script>
import SearchBar from "./components/SearchBar.vue";

import axios from "axios";
import { store } from "./store.js";
import AppMain from "./components/AppMain.vue";

export default {
  components: {
    SearchBar,
    AppMain,
  },
  data() {
    return {
      store,
    };
  },

  methods: {
    fetchResults(term) {
      this.fetchMovies(term);
      this.fetchTVSeries(term);
    },
    fetchMovies(query) {
      axios
        .get(
          `${store.url}/search/movie?api_key=${store.api_key}&query=${query}`
        )
        .then((response) => {
          const films = response.data.results.map((film) => {
            return {
              title: film.title,
              original_title: film.original_title,
              original_language: film.original_language,
              vote_average: Math.ceil(film.vote_average / 2),
              poster_path: film.poster_path,
            };
          });
          store.filmList = films;
        });
    },
    fetchTVSeries(query) {
      axios
        .get(`${store.url}/search/tv?api_key=${store.api_key}&query=${query}`)
        .then((response) => {
          const tvSeries = response.data.results.map((tvSerie) => {
            return {
              title: tvSerie.name,
              original_title: tvSerie.original_name,
              original_language: tvSerie.original_language,
              vote_average: Math.ceil(tvSerie.vote_average / 2),
              poster_path: tvSerie.poster_path,
            };
          });
          store.TVSeriesList = tvSeries;
        });
    },
  },
};
</script>

<template>
  <SearchBar @search="fetchResults"></SearchBar>
  <div class="container">
    <AppMain></AppMain>
  </div>
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
