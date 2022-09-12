<template>
  <div id="app">
    <HeaderComponents @onResponse="filteredMovies"/>
    <CardMovie v-for="movie in movies" :key="movie.id" :movie="movie" />
  </div>
</template>

<script>
import HeaderComponents from './components/HeaderComponents.vue';
import CardMovie from './components/CardMovie.vue';
  
export default {
  name: 'App',
  components: {
    HeaderComponents,
    CardMovie,
  },
  data() {
    return {
      movies: [],
      tvSeries: [],
      api_key: 'ab0c47b7b4ecf2838075c86d8541abac',
      api_URI: 'https://api.themoviedb.org/3',
      query: '',
    }
  },
  methods: {
    filteredMovies(movies) {
      this.movie = movies;
    }
    // getTvSeries() {
    //   axios.get(`${this.api_URI}/search/tv`,{
    //     params: {
    //       api_key: this.api_key,
    //       query: this.query
    //     }
    //   })
    //   .then((res) => {
    //     console.log(res.data.results)
    //     this.tvSeries = res.data.results;
    //   })
    // }
  }
}
</script>




<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
