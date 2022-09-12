<template>
  <div class="card">
    <h2 class="title">
      {{ movie.title }}
    </h2>
    <h1 class="original__title">
      {{ movie.original_title }}
    </h1>
    <p class="language">{{ movie.original_language }}</p>
    <p class="vote">{{ movie.vote_average }}</p>
  </div>
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