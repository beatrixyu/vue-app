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
    <h2>{{name}}</h2>
    <div v-once>
      <button v-on:click="changeName, incrementFunc(2)">click</button>
    </div>
    <button v-on:mouseover="name='Chris'">mouseover</button>
    
    <h2>{{count}}</h2>
    <button @click="count+=1">increment</button>
    <button @click="count-=1">decrement</button>
    <button @click="incrementFunc(5)">increment 5</button>
    <button @click="decrementFunc(5)">decrement 5</button>
    
    <pre>{{JSON.stringify(formValue, null,2)}}</pre>
    <form action="submit" @submit.prevent="onSubmit">
      <div>
        <label for="name">name</label>
        <input type="text" id="name" v-model.trim="formValue.name">
      </div>
      <div>
        <label for="profile">Profile</label>
        <textarea type="text" id="profile" v-model.trim="formValue.profile"/>
      </div>
      <div>
        <label for="country">Choose I place you wanna live</label>
        <select name="country" id="country" v-model="formValue.country">
          <option value="">Select a country</option>
          <option value="USA">USA</option>
          <option value="England">England</option>
          <option value="Germany">Germany</option>
        </select>
      </div>
      <div>
        <label for="jobLocation">Choose I place you wanna work</label>
        <select name="jobLocation" id="jobLocation" multiple v-model="formValue.jobLocation">
          <option value="USA">USA</option>
          <option value="England">England</option>
          <option value="Germany">Germany</option>
        </select>
      </div>
      <div>
        <input type="checkbox" name="remoteWork" id="remoteWork" v-model="formValue.remoteWork" true-value="yes" false-value="no">
        <label for="remoteWork">Open to remote work?</label>
      </div>
      <div>
        <input type="checkbox" value="react" id="react" v-model="formValue.techSet">
        <label for="react">react</label>
        <input type="checkbox" value="vue" id="vue" v-model="formValue.techSet">
        <label for="vue">Vue</label>
        <input type="checkbox" value="javascript" id="javascript" v-model="formValue.techSet">
        <label for="javascript">Javascript</label>
      </div>
      <div>
        <input type="radio" value="1-2" id="year" v-model="formValue.yearsOfExperience">
        <label for="yearsOfExperience">1-2</label>
        <input type="radio" value="2-5" id="year" v-model="formValue.yearsOfExperience">
        <label for="yearsOfExperience">2-5</label>
        <input type="radio" value="5+" id="year" v-model="formValue.yearsOfExperience">
        <label for="yearsOfExperience">5+</label>
      </div>
      <div>
        <input type="number" name="age" id="age" v-model="formValue.age" true-value="yes" false-value="no">
        <label for="age">Age</label>
      </div>
      <button>Submit</button>
    </form>

    <div> items total price - {{items.reduce((total, current)=>total = total + current.price, 0)}}</div>
    <div> total price - {{total}}</div>
    <div>push new items total price - {{total}}</div> <button @click="items.push({id:4, price:19, title:'duck'})">add new item</button>
    <h2 v-for="item in bigPet" :key="item.id">
      {{item.title}}
    </h2>
    <div>
    <h2>set and get - {{fullname}}</h2>
    <button @click="changeFullName">change the name</button>
    <div>
      <h2>{{volumn}}</h2>
      <button @click="volumn += 2">increase</button>
      <button @click="volumn -= 2">decrease</button>

    </div>

    </div>
    <div>
      <input type="text" v-model="movie">
      {{movie}} 
      <input type="text" v-model="movieInfo.title">
      {{movieInfo.title}}
      <input type="text" v-model="movieInfo.actor">
      <button @click="movieList.push('new')">Add movie</button>
      <h2>{{movieList}}</h2>
    </div>
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
    basicNum: 4,
    count:0,
    formValue:{
      name:'',
      profile:'',
      country:'',
      jobLocation: [],
      remoteWork: 'no',
      techSet:[],
      yearsOfexperience:'',
      age:'',
    },
    items:[
      {
        id:1,
        price:23,
        title:'cat'
      },
            {
        id:2,
        price:33,
        title:'dog'
      },      {
        id:3,
        price:13,
        title:'hamster'
      },
    ],
    firstname:'bea',
    lastname:'blome',
    volumn: 10,
    movie:'',
    movieInfo:{
      title:'',
      actor:''
    },
    movieList:[
      'harry pottey',
      'little women'
    ]
  }
},
methods:{
    mutiple(num){
        return num*this.basicNum
    },
    add(x,y,z){
      return x+y+z
    },
    incrementFunc(num){
     this.count += num
    },
    decrementFunc(num){
     this.count -= num
    },
    ChangeName(){
      return this.name = 'chris'
    },
    onSubmit(event){
     event.preventDefault();
     console.log('formvalue', this.formValue)
     //under the target in the event console
    },
    changeFullName(){
      this.fullname='chris jose blome'
    },
},
computed: {
  total(){
    return this.items.reduce((total, current)=>total = total + current.price, 0)
  },
  bigPet(){
    return this.items.filter(item =>item.price > 15)
  },
  fullname:{
    get(){
      return `${this.firstname} ${this.lastname}`
    },
    set(value){
      const fullname = value.split(' ')
      this.firstname = fullname[0]
      this.lastname = fullname[1]
    }
  },
},
 watch:{
   volumn(newVolumn, currVolumn){
     if(newVolumn > currVolumn && newVolumn === 16){
       alert('volumn is too high')
     }
   },
   movie: {
     handler(newValue){
     console.log(`watcher API is calling ${newValue}`)
     },
     immediate:true //immediate is used to call the api initially
   },
   movieInfo:{
     handler(newValue){
     console.log(`watcher API is calling ${newValue.title}and ${newValue.actor}`)
     },
     deep:true //deep object is used to call the deep nested value
   },
   movieList:{
     handler(newValue){
      console.log(`watcher API is calling ${newValue}`)
     },
     deep:true
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
