<template>
  <div id="app">
    <ul>
      <li v-for="movie in movies" :key="movie.id">
        {{ movie.original_title }}
      </li>
    </ul>
  </div>
</template>

<script>


import axios from 'axios';

export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      movies: [],
      api_key: 'ab0c47b7b4ecf2838075c86d8541abac',
      api_URL: 'https://api.themoviedb.org/3',
      query: 'ritorno'
    }
  },
  methods: {
    getMovies() {
      axios.get(`${this.api_URL}/search/movie?`,{
        params: {
          api_key: this.api_key,
          query: this.query
        }
      })
      .then((res) => {
        console.log(res);
        this.movies = res.data.results;
      })
    },
    beforeMount() {
      this.getMovies
    },
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
