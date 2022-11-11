<template>
  <div 
    @click="lineText"
    :class="{ isCompleted: this.toggle }"
  >

  <p>{{item}}</p>

    <!-- <span v-if="toggle">{{item}}</span>
    <span v-else>{{item}}</span> -->
  </div>
</template>

<script>

export default {
  name: 'WatchListItem',
  props: {
    item: String,
  },
  data(){
    return {
      toggle: false
    }
  },
  methods: {
    lineText(){
      this.toggle = !this.toggle
    }
  }


}
</script>

<style>
.isCompleted {
  text-decoration: line-through;
  color: grey
}
</style>