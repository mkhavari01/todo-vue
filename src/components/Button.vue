<template>
    <button :style="{background : color}">
        {{title}}
    </button>
</template>

<script>
export default {
    name : "Button",
    props : {
        title : String,
        color : String,
    },
}
</script>
<style scope>
    button {
        padding: 10px;
        outline: none;
        border: none;
        color: #242424;
        font-size: 13px;
        cursor: pointer;
        margin: 0 7px;
    }
</style>