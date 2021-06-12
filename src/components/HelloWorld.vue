<template>
  <div class="hello">
    
    <h1>
      name:{{name}}
    </h1>
    <p v-text='title' class="underline"></p>
    <p v-html='showAlert' ></p>
    <button v-bind:disabled="isDisabled">bind </button>
    <div v-bind:class='status'>dynamic class for status</div>
    <div v-bind:class="isSuccess? 'success' : 'danger'">Is success or danger?</div>
    <div v-bind:class="[isGood && 'good',isSuccess? 'success' : 'danger']">Array conditional statement</div>
    <!-- if isGood is true, the 'good' class is applied -->
    <div v-bind:class="{ //runs from the first to the end until find the class with the true statement and apply the style on the UI, can be mutiple classes
      good:!isGood,
      danger:!isSuccess,
      'success':isSuccess
    }">Object conditional statement</div>
    <div v-bind:style="{
      color: headerColor,
      'font-size': headerSize + 'px',
      marginTop: '100px'
    }">Style - inline style</div>
    <div v-bind:style="packageStyle">Style Object</div>
    <div v-if="num === 0">Number is 0</div>
    <div v-else-if="num > 0">Number is more than 0</div>
    <div v-else-if="num < 0">Number is less than 0</div>

    <div v-else>Number is NOT  0</div>
    <div v-show="isShow">v-show </div>
    <div>number calculator - {{mutiple(2)}}</div>
    <div>number calculator - {{add(2,3,4)}}</div>


  </div>
</template>

<script>
export default {
  name:'vue-app',
  data(){
  return {
    name:'Bea Blome',
    title:'software developer',
    showAlert: `<button onclick="alert('yes')">click</button>`,
    status:'danger',
    isDisabled:true,
    isGood:true,
    isSuccess: true,
    headerColor: 'yellow',
    headerSize: 50,
    packageStyle:{
      fontSize: '50px',
      'margin-top':'20px',
      color:'orange',
    },
    num:8,
    isShow:true,
    basicNum: 4
  }
},
methods:{
    mutiple(num){
        return num*this.basicNum
    },
    add(x,y,z){
      return x+y+z
    }

},
}
</script>
<style scoped>
.underline{
  color:purple;
  text-decoration: underline;
}
.success {
  color: green;
}
.danger{
  color:red
}
.good {
  color:blue
}

</style>
