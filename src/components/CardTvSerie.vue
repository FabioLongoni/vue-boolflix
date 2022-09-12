<template>
  <li class="card">
    <h4 class="title">
      {{ tvSerie.name }}
    </h4>
    <h5 class="original__title">
      {{ tvSerie.original_name }}
    </h5>
    <img :src="require(`../assets/${tvSerie.original_language}.png`)" alt="">{{ tvSerie.original_language }}
    <p class="vote">{{ tvSerie.vote_average }}</p>
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

<style>

</style>