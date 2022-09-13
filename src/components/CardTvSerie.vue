<template>
  <li class="card">
    <h4 class="title">
      {{ tvSerie.name }}
    </h4>
    <h5 class="original__title">
      {{ tvSerie.original_name }}
    </h5>
    <img class="flag" :src="tvSerie.flag" alt="">
    <p class="language">{{ tvSerie.lang }}</p>
    <p class="vote">{{ tvSerie.vote_average }}</p>
    <img :src="tvSerie.poster" alt="">
  </li>
</template>

<script>
export default {
  props: {
    tvSerie: {
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
</style>