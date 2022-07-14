<template>
  <div class="app">
    <HeaderComponent @performeSearch="search" />
    <MainComponent 
    :movieCards="movies"
    :serieCards="series"
    :searching="searchStarted"
    />

  </div>
</template>

<script>
import axios from 'axios';
import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'


export default {
  nome: 'app',
  components: {
    HeaderComponent,
    MainComponent
  },
  data() {
    return {
      apiUrlFilm:  'https://api.themoviedb.org/3/search/movie?api_key=9702a6631dc530207a004d510a940372&language=en-US&page=1&include_adult=false',
      apiUrlSerie: 'https://api.themoviedb.org/3/search/tv?api_key=9702a6631dc530207a004d510a940372&language=en-US&page=1&include_adult=false',
      movies: [],
      series: [],
      allResults: [],
      searchStarted: false
    }
  },
  methods: {
    getMovies(apiParams) {
      axios
          .get(this.apiUrlFilm + 'movies', apiParams)
          .then((response) => {
            this.movies = response.data.results;
            this.allResults = [...this.movies];
            this.searchStarted = true;
          })
          .catch((error) => {
            console.log('error', error);
          });
    },
    getSeries(apiParams) {
      axios
          .get(this.apiUrlSerie + 'series', apiParams)
          .then((response) => {
            this.series = response.data.results;
            this.allResults = [...this.series];
            this.searchStarted = true;
          })
          .catch((error) => {
            console.log('error', error);
          });
    },
    search: function (searchText) {
      
      const paramsObj = {
        params: {
          query: searchText,
          language: 'it-IT'
        }
      };
      this.getMovies(paramsObj);
      this.getSeries(paramsObj);
    
    }
  } 
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>