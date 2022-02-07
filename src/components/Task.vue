<template>
    <section :class="[task.reminder ? 'reminder' : '' ]">
        <h3 class="h3"> 
            <span>{{task.id}}</span>
            <span>{{task.text}}</span>
        </h3>
        <div class="btn-holder">
            <!-- <button>
                DELETE
            </button>
            <button>
                UPDATE
            </button> -->
            <Button title="UPDATE" color="#0000ff91" />
            <Button title="DELETE" color="#c71921ba"  @click="onDelete(task.id)" />
        </div>
    </section>
</template>
<script>

import Button from './Button.vue'

export default {
    name : "Task",
    props : {
        task : Object,
    },
    components : {
        Button
    },
    methods : {
        onDelete : function(id){
            this.$emit('delete-task',id)
        }
    }
}
</script>
<style scope>
    section {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin: 10px 0;
        background-color: gainsboro;
    }
    .h3 {
        display: flex;
        justify-content: flex-start;
        align-items:  center;
    }
    .h3 span {
        padding: 0 10px;
    }
    .reminder {
        border-left: solid 4px green;
    }
</style>