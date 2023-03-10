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
          store.filmList = response.data.results;
        });
    },
    fetchTVSeries(query) {
      axios
        .get(`${store.url}/search/tv?api_key=${store.api_key}&query=${query}`)
        .then((response) => {
          store.TVSeriesList = response.data.results;
        });
    },
  },
};
</script>

<template>
  <SearchBar @search="fetchResults"></SearchBar>
  <div class="container">
    <AppMain :filmList="filmList"></AppMain>
  </div>
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
