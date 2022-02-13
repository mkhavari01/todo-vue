<template>
    <div v-for="(task,index) in tasks" :key="task.id" :id="task.id" >
        <!-- <h3>
            {{task.id}} ... {{task.text}}
        </h3> -->
        <Task @delete-task="$emit('delete-task',task.id)" :task="task" :index="index" @update-task="updateHandler" />
    </div>
</template>
<script>

import Task from './Task.vue'

export default {
    name : "Tasks",
    props : {
        tasks : Array,
    },
    components : {
        Task
    },
    emits : ['delete-task',"update-task"],
    methods : {
        updateHandler : function(updatedTask){
            this.$emit('update-task',updatedTask)
        }
    }
}
</script>
<style>
    
</style>