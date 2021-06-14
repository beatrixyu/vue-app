<template>
    <div>
      This is popup child component,
      <br>
      click the button to close the Popup
      <br>
      and pass data back to parent app component.
      <input type="text" v-model="childValue">
     <button @click="$emit('close',childValue)">close popup</button>
    </div>
</template>

<script>
    export default {
        name:'Popup',
        // emits:['close'],
        emits:{
            //validation the input value which will be send back to parent component,
            //emits becomes object || close is the property name and the value is validation function
            close:(childValue)=>{
                if(!childValue){
                    return false
                } else {
                    return true
                }

            }
        },
        data(){
        return{
            childValue:''
        }
    }

    }
    

</script>

<style scoped>

</style>