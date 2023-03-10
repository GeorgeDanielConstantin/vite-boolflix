<script>
export default {
  props: {
    title: String,
    original_title: String,
    original_language: String,
    vote_average: Number,
    poster_path: Number,
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
  <div class="col gy-5">
    <div class="card">
      <div class="card-front">
        <img
          class="card-img"
          :src="'https://image.tmdb.org/t/p/w342' + poster_path"
          alt=""
        />
      </div>
      <div class="card-desc">
        <p>Titolo: {{ title }}</p>
        <p>Titolo originale: {{ original_title }}</p>
        <p>
          <img :src="getFlag(original_language)" alt="" />
        </p>
        <p>
          Rating:
          <font-awesome-icon icon="fa-sopd fa-star" v-for="i in vote_average" />
          <font-awesome-icon
            icon="fa-regular fa-star"
            v-for="i in 5 - vote_average"
          />
        </p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  height: 500px;
  background-color: #222;

  .card-front {
    height: 100%;
    overflow: hidden;
    .card-img {
      width: 100%;
    }
  }
  .card-desc {
    display: none;
    height: 100%;
    overflow: auto;
  }

  &:hover {
    .card-front {
      display: none;
    }
    .card-desc {
      display: block;
      background-color: #222;
    }
  }
}
</style>
