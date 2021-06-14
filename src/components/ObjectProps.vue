<template>
    <div>
    my name is {{name}}, I am {{age}} years old, I am {{isMarried?'married':'single'}}
    </div>
</template>

<script>
    export default {
        name:'Object',
        props:{
            name:String,
            age:Number,
            isMarried:Boolean,
        }
    }
</script>

<style lang="scss" scoped>

</style>