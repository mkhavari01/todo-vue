<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <Header @add-task="addTask" title="Task Tracker" />
  <Tasks :tasks="tasks" @delete-task="deleteTask" />
</template>

<script>

import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data(){
    return {
      tasks : [],
    }
  },
  async created(){
    this.tasks = await this.fetchData()
  },
  methods : {
    deleteTask(id) {
      axios.delete(process.env.VUE_APP_AXIOS_URL+`/${id}`).then((res)=>{
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }).catch((err)=>{
        console.log(err)
      })
    },
    addTask(desc){
      axios.post(process.env.VUE_APP_AXIOS_URL,{
        id : this.tasks.length + 1,
        text : desc,
        reminder : false
      }).then((res)=>{
        console.log('res',res)
        this.tasks = [...this.tasks,res.data]
      })
    },
    async fetchData(){
      const res = await axios.get(process.env.VUE_APP_AXIOS_URL);
      return res.data
    }
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
