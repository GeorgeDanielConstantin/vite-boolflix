<script>
import { store } from "../store.js";
import Card from ".//Card.vue";

export default {
  data() {
    return {
      store,
    };
  },

  components: {
    Card,
  },
};
</script>

<template>
  <div class="row row-cols-3">
    <Card
      v-for="film in store.filmList"
      :title="film.title"
      :original_title="film.original_title"
      :original_language="film.original_language"
      :vote_average="film.vote_average"
      :poster_path="film.poster_path"
    ></Card>
  </div>

  <div class="row row-cols-3">
    <Card
      v-for="serie in store.TVSeriesList"
      :title="serie.title"
      :original_title="serie.original_title"
      :original_language="serie.original_language"
      :vote_average="serie.vote_average"
      :poster_path="serie.poster_path"
    ></Card>
  </div>
</template>

<style scoped></style>
