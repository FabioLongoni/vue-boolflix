<template>
  <div id="app">
    <HeaderComponents @onResponse="filteredProgram"/>
    <h3>Movies</h3>
    <ul>
      <CardMovie v-for="movie in movies" :key="movie.id" :movie="movie" />
    </ul>
    <h3>tvSeries</h3>
    <ul>
      <CardTvSerie v-for="tvSerie in tvSeries" :key="tvSerie.id" :tvSerie="tvSerie"/>
    </ul>
  </div>

</template>

<script>
import HeaderComponents from './components/HeaderComponents.vue';
import CardMovie from './components/CardMovie.vue';
import CardTvSerie from './components/CardTvSerie.vue';
  
export default {
  name: 'App',
  components: {
    HeaderComponents,
    CardMovie,
    CardTvSerie
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
    // filteredMovies(movies) {
    //   this.movies = movies;
    // },
    filteredProgram(tvSeries,movies) {
      this.tvSeries = tvSeries;
      this.movies = movies;
    }
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
  ul {
    display: flex;
    flex-wrap: wrap;
    flex-basis: 200px;
    gap: 1rem;
  }
}
</style>
