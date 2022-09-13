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
        <strong>Vote : </strong>
        <font-awesome-icon class="star__icon" v-for="n in el.vote" :key="n" icon="fa-solid fa-star" />
        <font-awesome-icon class="star__icon" v-for="n in (5 - el.vote)" :key="n + el.vote" icon="fa-regular fa-star" /> 
      </div>
      <div>
        <strong>Overview :</strong> {{el.overview}}
      </div>
    </div>
    <img class="bg" v-if="el.poster" :src="el.poster" alt="">
    <img v-else src= 'https://picsum.photos/342/300' alt="">
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

</style>