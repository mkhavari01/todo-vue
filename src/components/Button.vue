<template>
    <button>
        {{title}}
    </button>
</template>
<script>
export default {
    name : "Button",
    props : {
        title : String
    }
}
</script>
<style scoped>
    button {
        padding: 10px;
        outline: none;
        border: none;
        background: gainsboro;
        color: #242424;
        font-size: 13px;
        cursor: pointer;
    }
</style>