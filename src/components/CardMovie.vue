<template>
  <li class="card">
    <h4 class="title">
      {{ movie.title }}
    </h4>
    <h5 class="original__title">
      {{ movie.original_title }}
    </h5>
    <img :src="movie.flag" alt="">
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

<style>

</style>