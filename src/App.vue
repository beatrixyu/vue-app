<template>
<div>
  <HelloWorld/>
 <Greet :username='name' :usertitle='title'/>
 <Greet username='name' usertitle='title'/>
 <Greet username='Bea' usertitle='Blome'/>
 <ObjectProps name='chris' :age='30' :isMarried='true'/>

 </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Greet from './components/Greet.vue'
import ObjectProps from './components/ObjectProps.vue'



export default {
  name: 'App',
  components: {
    HelloWorld,
    Greet,
    ObjectProps,
  },
  data(){
    return {
      name:'yes hallo',
      title:'developer'
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
