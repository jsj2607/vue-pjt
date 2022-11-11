<template>
  <form @submit.prevent="createWatchList">
    <input 
      type="text" 
      v-model="watchListTitle"
    >
    <input type="submit">
  </form>
</template>

<script>
export default {
  name: 'WatchListForm',
  data() {
    return {
      watchListTitle: null,
    }
  },
  methods: {
    createWatchList(){
      localStorage.setItem("movielist", this.watchListTitle)
      // console.log(this.watchListTitle)
      this.$emit('create-watch-list', this.watchListTitle)
      this.watchListTitle = null
    }
  }
}
</script>

<style>

</style>