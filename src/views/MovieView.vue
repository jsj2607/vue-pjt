<template>
  <div>
    <h1>Movie View</h1>
    <div class="container text-center">
      <div class="row">
        <br>
        <MovieCard
          class="col-4"
          v-for="(movie, index) in movies" 
          :movie="movie" 
          :key="index" />
      </div>
    </div>
  </div>

</template>

<script>
import axios from 'axios'
import MovieCard from '@/components/MovieCard'


export default {
  name: 'MovieView',
  components: {
    MovieCard,
  },
  data() {
    return {
      movies: null,
    }
  },
  methods: {
    getMovies() {
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
          // const imgSrc = response.data
        })
        .catch((error) => {
          console.log(error)
        })
    }
  },
  created() {
    this.getMovies()
  }
}
</script>

<style>

</style>


