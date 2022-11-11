<template>
  <div>
    <h1>Random View</h1>
    <button @click="pickMovie">Pick!</button>
    <br><br>
    <img v-if="movies" :src="imgSrc" alt="#">
    <h1 v-if="movies">{{ movies[a_number].title }}</h1>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'RandomView',
  data() {
    return {
      listLength: null,
      movies: null,
      a_number: null,
    }
  },
  computed: {
    imgSrc(){
      return `https://image.tmdb.org/t/p/w300${this.movies[this.a_number].poster_path}`
    }
  },
  methods: {
    pickMovie() {
      const moviesURL = 'https://api.themoviedb.org/3/movie/top_rated?'
      const parameters = {
        api_key: '48e76cf87ff80b385a6ee149be709745',
        page: 10,
        language: 'en_US'
      }
      axios({
        method: 'get',
        url: moviesURL,
        params: parameters
      })
        .then((response) => {
          console.log(response)
          console.log(response.data.results)
          this.movies = response.data.results
          this.listLength = this.movies.length
          this.a_number = Math.floor((Math.random() * this.listLength))
        })
        .catch((error) => {
          console.log(error)
        })
      
      
    }
  },
  created() {
    this.pickMovie()
  }
}
</script>

<style>

</style>

//  석진아 화이팅하렴. 키보드가 상당히 부드럽고 좋네 ㅎㅎ

// 혼자하는게 나았을 지도 모르겠는데, 갑자기 희진이가 같이 하자해서 많이 당황했지 ?
// 이 또한 지나갈 것이여
// 스펙타클한 사회다 ...