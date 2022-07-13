<template>
  <div class="app">
    <HeaderComponent @performeSearch="search" />

    <MainComponent 
    :movieCards="movies"
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
      apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=9702a6631dc530207a004d510a940372&language=en-US&page=1&include_adult=false',
      movies: [],
      series: [],
      allResults: [],
      searchStarted: false
    }
  },
  methods: {
    getMovies(apiParams) {
      axios
          .get(this.apiUrl + 'movies', apiParams)
          .then((response) => {
            this.movies = response.data.results;
            this.allResults = [...this.movies];
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
    
    }
  } 
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>


