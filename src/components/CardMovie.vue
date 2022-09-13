<template>
  <li class="card">
    <h4 class="title">
      {{ movie.title }}
    </h4>
    <h5 class="original__title">
      {{ movie.original_title }}
    </h5>
    <img class="flag" :src="movie.flag" alt="">
    <!-- <img class="flag" src="../assets/it.png" alt=""> -->
    <p class="language">{{ movie.lang }}</p>
    <p class="vote">{{ movie.vote }}</p>
    <img :src="movie.poster" alt="">
  </li>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
  .card {
    border: 1px solid #dadada;
  }
  .flag {
    width: 100px;
  }
  
</style>