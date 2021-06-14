<template>
    <div>
       Greet {{username}} {{usertitle}}
    </div>
</template>

<script>
    export default {
        name: 'Greet',
        props:['username','usertitle']
    }
</script>

<style scoped>

</style>