<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <Header title="Task Tracker" />
  <Tasks :tasks="tasks" />
</template>

<script>

import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data(){
    return {
      tasks : []
    }
  },
  created(){
    this.tasks = [{
      id : 1,
      text : 'see doctor',
      reminder : true,
    },{
      id : 2,
      text : 'go to Gym',
      reminder : true,
    },{
      id : 3,
      text : 'feed pets',
      reminder : false,
    }]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  max-width: 700px;
  margin: auto;
}
</style>
