<template>
    <div>
        <h2>custom styled input</h2>
    <input type="text" 
           @input="$emit('update:modelValue', $event.target.value)">
           //in order to send data from the styled input to the app component, have to use emit and $event.target.value
    </div>
</template>

<script>
    export default {
        data(){
            return {
                name:'Input',
                props: {
                    modelValue: String
                }
            }

        }
    }
</script>

<style scoped>
input[type='text']{
    height:20px;
    width: 80%;
    border-color: pink
}
</style>