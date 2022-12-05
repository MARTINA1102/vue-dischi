<template>
  <div>
    <HeaderPage :genres-list="genresList"
      @changedGenre="genreChange"/>
    <MainPage @genresReady="getGenresList" :genre-filter="genreFilter"/>
    <FooterPage />
  </div>
</template>

<script>
import HeaderPage from './components/HeaderPage.vue';
import MainPage from './components/MainPage.vue';
import FooterPage from './components/FooterPage.vue';

export default {
  components: {
    HeaderPage,
    MainPage,
    FooterPage,
  },
  data() {
    return {
      genresList: [],
      genreFilter: 'All',
    };
  },
  methods: {
    getGenresList(genresList) {
      this.genresList = genresList;
    },
    genreChange(genreFilter) {
      this.genreFilter = genreFilter;
    },
  },
};
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
}

</style>
