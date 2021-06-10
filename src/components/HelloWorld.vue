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
    isSuccess: true
  }
}
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
