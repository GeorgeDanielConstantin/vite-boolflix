<script>
export default {
  props: {
    title: String,
    original_title: String,
    original_language: String,
    vote_average: Number,
  },

  methods: {
    getFlag(country) {
      country = country.toUpperCase();

      return "https://flagsapi.com/" + country + "/flat/64.png";
    },
  },
};
</script>

<template>
  <ul class="col">
    <li>title: {{ title }}</li>
    <li>original_title: {{ original_title }}</li>
    <li>
      <img :src="getFlag(original_language)" alt="" />
    </li>
    <li>vote_average: {{ vote_average }}</li>
  </ul>
</template>

<style lang="sass" scoped></style>
