<script>
export default {
  data() {
    return {
      term: "",
    };
  },
  emits: ["search"],
};
</script>

<template>
  <nav class="navbar navbar-dark">
    <div class="container">
      <a class="navbar-brand"></a>
      <form
        class="d-flex"
        role="search"
        @submit.prevent="$emit('search', term)"
      >
        <input
          v-model="term"
          class="form-control me-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
        />
        <button class="btn btn-primary" type="submit">Search</button>
      </form>
    </div>
  </nav>
</template>

<style lang="sass" scoped></style>
