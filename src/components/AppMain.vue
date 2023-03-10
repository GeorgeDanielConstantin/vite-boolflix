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
    ></Card>
  </div>

  <div class="row row-cols-3">
    <Card
      v-for="serie in store.TVSeriesList"
      :title="serie.name"
      :original_title="serie.original_name"
      :original_language="serie.original_language"
      :vote_average="serie.vote_average"
    ></Card>
  </div>
</template>

<style scoped></style>
