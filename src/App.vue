<template>
  <div id="app">
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        {{ movie.original_title }}
      </li>
      <li v-for="serie in tvSeries" :key="serie.id">
        {{ serie.name}}
      </li>
    </ul>
  </div>
</template>

<script>
  import axios from 'axios';
  
  export default {
    name: 'App',
    data() {
      return {
        movies: [],
        tvSeries: [],
        api_key: 'ab0c47b7b4ecf2838075c86d8541abac',
        query: 'pippo',
        api_URI: 'https://api.themoviedb.org/3'
      }
    },
    methods: {
      getMovies() {
        axios.get(`${this.api_URI}/search/movie`,{
          params: {
            api_key: this.api_key,
            query: this.query
          }
        })
        .then((res) => {
          console.log(res.data.results)
          this.movies = res.data.results;
        })
      },
      getTvSeries() {
        axios.get(`${this.api_URI}/search/tv`,{
          params: {
            api_key: this.api_key,
            query: this.query
          }
        })
        .then((res) => {
          console.log(res.data.results)
          this.tvSeries = res.data.results;
        })
      }
    },
    beforeMount() {
      this.getMovies()
      this.getTvSeries()
    }
  }
</script>




<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
