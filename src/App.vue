<template>
  <div id="app">
    <HeaderComponents @onResponseMovies="filteredMovies" @onResponseTvSeries="filteredTvSeries" />
    <div class="main__container">
      <h3>Movies :</h3>
      <ul>
        <Card v-for="movie in movies" :key="movie.id" :el="movie" />
      </ul>
      <h3>Tv Series :</h3>
      <ul>
        <Card v-for="tvSerie in tvSeries" :key="tvSerie.id" :el="tvSerie"/>
      </ul>
    </div>
  </div>

</template>

<script>
import HeaderComponents from './components/HeaderComponents.vue';
import Card from './components/CardComponent.vue';
import "@fontsource/montserrat";
  
export default {
  name: 'App',
  components: {
    HeaderComponents,
    Card
},
  data() {
    return {
      flags: ['au','en','it','es','de','rs','us','jp','fr','ru'],
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
          flag: this.flags.includes(el.original_language) ? require(`@/assets/${el.original_language}.png`) : null,
          poster:`${this.posterBaseUri}w342${el.poster_path}`,
          vote: Math.round(el.vote_average / 2),
          overview: el.overview
        }
        return newMovie;
      })
    },
    tvSeries() {
      return this.originalTvSeries.map((el) => {
        const newTvSeries = {
          id: el.id,
          title: el.name,
          original_title: el.original_name,
          lang: el.original_language,
          flag: this.flags.includes(el.original_language) ? require(`@/assets/${el.original_language}.png`) : null,
          poster: `${this.posterBaseUri}w342${el.poster_path}`,
          vote: Math.round(el.vote_average / 2),
          overview: el.overview
        }
        return newTvSeries;
      })
    }
  },
  methods: {
    filteredMovies(movies) {
      this.originalMovies = movies;
    },
    filteredTvSeries(tvSeries) {
      this.originalTvSeries = tvSeries;
    },
  }
}
</script>




<style lang="scss">
@import './style/style.scss';


</style>
