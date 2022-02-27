<template>
  <div id="app">
    <myHeader @selectedGenreEvt="setSelectedGenre" :genresList="genresList"/>
    <myMain @genresReady="setGenres" :selectedGenre="selectedGenre"/>
  </div>
</template>

<script>
import myHeader from './components/myHeader.vue'
import myMain from './components/myMain.vue'

export default {
  name: 'App',
  components: {
    myHeader,
    myMain,
  },
  data() {
    return {
      genresList: [],
      selectedGenre: '',
    }
  },
  methods: {
    setGenres(genresListEvt) {
      this.genresList = genresListEvt;
    },
    setSelectedGenre(selectedGenreEvt) {
      this.selectedGenre = selectedGenreEvt;
    }
  }
}
</script>

<style>
  @import "./assets/style/general.scss";
</style>
