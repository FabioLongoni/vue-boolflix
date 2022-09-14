<template>
  <div class="container">
    <div id="header__components">
    <h1 id="name__app">
      BoolFlix
    </h1>
    <div class="input">
      <input class="text" type="text" v-model="query" placeholder="search" @keyup.enter="getBoth">
      <input class="btn" type="button" value="search" @click="getBoth">
    </div>
  </div>
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
    getBoth() {
      this.getMovies();
      this.getTvSeries();
    },
    getMovies() {
      if(this.query.trim() === '')
        return
      axios.get(`${this.api_URI}/search/movie`,{
        params: {
          api_key: this.api_key,
          query: this.query.trim()
        }
      })
      .then(res => {
        console.log(res.data.results)
        this.$emit('onResponseMovies', res.data.results);
      })
    },
    getTvSeries() {
      if(this.query.trim() === '')
        return
      axios.get(`${this.api_URI}/search/tv`,{
        params: {
          api_key: this.api_key,
          query: this.query.trim()
        }
      })
      .then((res) => {
        console.log(res.data.results)
        this.$emit('onResponseTvSeries',res.data.results);
      })
    },
  }
}
</script>

<style lang="scss"  scoped>
@import '../style/HeaderComponents';

</style>