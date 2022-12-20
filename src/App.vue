
<template>
<!--Data Entry-->
<h2> Name- {{name}}</h2>
<h2> Address- {{address}}</h2>
<h2> DOB- {{dob.toISOString().substr(0, 10)}}</h2>
<!--Age-->
<form @click="calculateAge">
  <button> Calculate age</button>
  <h2 v-if="showElement">Age- {{age}}</h2>
</form>
<!--validation-->
<div @click="validateAge">
  <button>Validate Age</button>
  <p v-if="showAge && age>=18" class="success">You are ok to use</p>
  <p v-else-if="showAge && age<18 && age>0" class="error">You are underage</p>
</div>
<!--Array data-->
<div v-for="user in userName" :key="user.first">
  <img :src="user.picture">
  <h2>
  Name- {{user.first}} <br> Age- {{user.age}}
  </h2>
</div>
  </template>

<script>
export default {
  name:'App',
  data(){
    return{
      name:'Rahul',
      address:'India',
      date: new Date(),
      dob: new Date("2010-01-01"),
      age:'',
      showElement: false,
      showAge: false,
      userName:[
      {first:'ABC' ,age:'20', picture: './img/img.png'},
      {first:'xyz', age:'30', picture:'./img/img.png'}]
    }
  },
  methods:{
    calculateAge(event){
      event.preventDefault();
      this.age = this.date.getFullYear() - this.dob.getFullYear()
      return this.age, this.showElement=true
    },
    validateAge(event){
      event.preventDefault();
      return  this.showAge=true
    }
  }
}
</script>


<style >
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  text-align: center;
  margin-top: 60px;
}
button{
  width: 200px;
  height: 40px;
  border-radius: 30px;
  font-size: 20px;
}
div{
  margin-top: 10px;
}
.error{
  color: red;
}
.success{
  color:green
}
img{
  width: 300px;
}

</style>
