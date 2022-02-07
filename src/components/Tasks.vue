<template>
    <div v-for="task in tasks" :key="task.id" >
        <!-- <h3>
            {{task.id}} ... {{task.text}}
        </h3> -->
        <Task @delete-task="$emit('delete-task',task.id)" :task="task" />
    </div>
</template>
<script>

import Task from './Task.vue'

export default {
    name : "Tasks",
    props : {
        tasks : Array
    },
    components : {
        Task
    },
    emits : ['delete-task']
}
</script>
<style>
    
</style>