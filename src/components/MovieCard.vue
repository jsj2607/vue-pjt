<template>
  <div>
    
    <img :src="imgSrc" alt="">
    <h1>{{ movie.title }}</h1>
    <p>{{ movie.overview }}</p>
    <br><br>
  </div>
</template>

<script>
export default {
  name: 'MovieCard',
  props: {
    movie: Object,
  },
  computed: {
    imgSrc(){
      return `https://image.tmdb.org/t/p/w300${this.movie.poster_path}`
    }
  }
}
</script>

<style>

</style>