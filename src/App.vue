<template>
<div>
  <HelloWorld/>
 <ArrayProps :username='name' :usertitle='title'/>
 <ArrayProps username='name' usertitle='title'/>
 <ArrayProps username='Bea' usertitle='Blome'/>
 <ObjectProps name='chris' :age='30' :isMarried='true'/>
 <button @click="showPopup=true">Show Popup</button>
 <Popup v-show="showPopup" @close="closePopup"/>
 <Input v-model="inputValue" /> 
 Normal input
 <input type="text" v-model="inputValue">

 </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ArrayProps from './components/ArrayProps.vue'
import ObjectProps from './components/ObjectProps.vue'
import Popup from './components/Popup.vue'
import Input from './components/Input.vue'


export default {
  name: 'App',
  components: {
    HelloWorld,
    ArrayProps,
    ObjectProps,
    Popup,
    Input
  },
  data(){
    return {
      name:'yes hallo',
      title:'developer',
      showPopup:false,
      inputValue:'',
    }
  },
  methods:{
    closePopup(childValue){
      this.showPopup=false
      console.log(`the value is rendered from the popup child component - ${childValue}`)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
