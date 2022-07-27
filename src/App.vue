<template>
  <div id="app">
    <Header
      :genres="selectedGenres"
      :authors="selectedAuthors"
      @newGenre="updateGenre"
      @newAuthor="updateAuthor"
      :watchGenre="activeGenre"
      :watchAuthor="activeAuthor"
    />
    <DiscContainer
      @discData="setData"
      :updatedGenre="activeGenre"
      :updatedAuthor="activeAuthor"
    />
  </div>
</template>

<script>
import BaseHeader from "./components/BaseHeader";
import DiscContainer from "./components/DiscContainer";
import Disc from "./components/Disc";

export default {
  name: "App",
  components: {
    BaseHeader,
    DiscContainer,
  },
  data() {
    return {
      selectedGenres: [],
      selectedAuthors: [],
      activeGenre: "",
      activeAuthor: ""
    };
  },
  methods: {
    setData: function (arrayGenres, arrayAuthors) {
      this.selectedGenres = arrayGenres;
      this.selectedAuthors = arrayAuthors;
    },
    updateGenre: function (genre) {
      this.activeGenre = genre;
      this.activeAuthor = "";
    },
    updateAuthor: function (author) {
      this.activeAuthor = author;
      this.activeGenre = "";

    }
  },
};
</script>

<style lang="scss">
@import "./scss/general";
</style>
