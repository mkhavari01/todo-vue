<template >
    <footer>
        <p>
            This is our footer
        </p>
        <router-link to="/about">
            Got to about page
        </router-link>
        
    </footer>
</template>
<script>
export default {
    name: "Footer",
}
</script>
<style scoped>
    footer {
        border : 1px solid gray;
        padding-bottom: 20px;
    }
</style>>
    