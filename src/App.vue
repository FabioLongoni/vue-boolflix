<template>
  <div id="app">
    <HeaderComponents @onResponse="filteredMovies"/>
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
      originalMovies: [],
      originalTvSeries: [],
      api_key: 'ab0c47b7b4ecf2838075c86d8541abac',
      api_URI: 'https://api.themoviedb.org/3',
      query: '',
      posterBaseUri:'https://image.tmdb.org/t/p/'
    }
  },
  computed: {
    movies() {
      return this.originalMovies.map((el) => {
        const newMovie = {
          id: el.id,
          title: el.title,
          original_title: el.original_title,
          lang: el.original_language,
          flag:`./assets/${el.original_language}.png`,
          poster: `${this.posterBaseUri}w342${el.poster_path}`,
          vote: Math.round(el.vote_average / 2)
        }
        return newMovie;
      })
    }
  },
  methods: {
    filteredMovies(movies) {
      this.originalMovies = movies;
    },
    // filteredProgram(tvSeries,movies) {
    //   this.originalTvSeries = tvSeries;
    //   this.originalMovies = movies;
    // }
  }
}
</script>




<style lang="scss">
@import './style/style.scss';

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
