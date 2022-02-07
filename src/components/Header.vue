<template >
    <header>
        <h1>{{title}}</h1>
        <div>
            <Button title="Add Task" color="gainsboro" :propFunc="addTaskHandler" />
            <!-- <Button title="Update Task" color="#0000ff91" />
            <Button title="delete Task" color="#15be41" /> -->
        </div>
    </header>
</template>
<script>

import Button from './Button.vue'

export default {
    name : "Header",
    props : {
        title : String,
    },
    components : {
        Button
    },
    methods : {
        addTaskHandler : function(){
            console.log('you clicked on Adding method')
        }
    }
}
</script>
<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>