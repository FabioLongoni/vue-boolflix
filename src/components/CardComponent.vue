<template>
  <li class="card">
    <div class="content_card">
      <div class="title">
        <strong>Title:</strong> {{ el.title }}
      </div>
      <div class="original__title">
        <strong>Original Title :</strong> {{ el.original_title }}
      </div>
      <div class="vote">
        <strong>Vote :</strong> {{ el.vote }}
      </div>
      <div>
        <strong>Overview :</strong> {{el.overview}}
      </div>
    </div>
    <img class="bg" v-if="el.poster" :src="el.poster" alt="">
  </li>
</template>

<script>
export default {
  props: {
    el: {
      type: Object,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '../style/cardComponent';

  .card {
    border: 1px solid #dadada;
  }
  
</style>