<template>
  <div>
    <h1>보고싶은 영화</h1>
    <WatchListForm @create-watch-list="createWatchList"/>
    <WatchListItem
    v-for="(item, index) in title"
    :key="index"
    :item="item"/>

  </div>
</template>

<script>
import WatchListItem from '@/components/WatchListItem'
import WatchListForm from '@/components/WatchListForm'

export default {
  name: 'WatchListView',
  components: {
    WatchListItem,
    WatchListForm,
  },
  data() {
    return {
      title: [],
    }
  },
  methods: {
    createWatchList(watchList){
      
      const movie = {
        title: watchList
      }
      console.log(movie)
      this.title.push(movie.title)
    },
  }
}
</script>

<style>

</style>