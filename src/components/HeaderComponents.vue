<template>
  <div id="header__components">
    <h1 id="name__app">
      Boolflix
    </h1>
    <input type="text" v-model="query" placeholder="search" @keyup.enter="getTvSeries">
    <input type="button" value="search" @click="getTvSeries">
  </div>
  
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      query: '',
      api_key: 'ab0c47b7b4ecf2838075c86d8541abac',
      api_URI: 'https://api.themoviedb.org/3',
    }
  },
  methods : {
    getMovies() {
      axios.get(`${this.api_URI}/search/movie`,{
        params: {
          api_key: this.api_key,
          query: this.query.trim()
        }
      })
      .then(res => {
        console.log(res.data.results)
        this.$emit('onResponse', res.data.results);
      })
    },
    getTvSeries() {
      axios.get(`${this.api_URI}/search/tv`,{
        params: {
          api_key: this.api_key,
          query: this.query.trim()
        }
      })
      .then((res) => {
        console.log(res.data.results)
        this.$emit('onResponse',res.data.results);
      })
    },
  }
}
</script>

<style>

</style>