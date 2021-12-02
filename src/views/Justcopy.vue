<template>
 <div class="container">
 <form id="app" @submit="checkForm">
  
 <p class="text-info">{{ error }}</p>

 <div>
  <label for="name" class="text-info">  <p>Check in</p> </label>
  <p><date-pick v-model="date" class="p-2"></date-pick></p>
 </div>
  <div>
  <label for="name" class="text-info">  <p>Check out</p> </label>
  <p><date-pick v-model="date" class="p-2"></date-pick></p>
 </div>
  <p>
    <input type="submit" value="Submit">  
  </p>
 <div class="row">
  <div class="col-md-4">
 
  </div>
  <div class="col-md-4">
  
  </div>
  <div class="col-md-4">
  
  </div>
  </div>
</form>
 </div>
</template>
<script>
import DatePick from 'vue-date-pick';
import 'vue-date-pick/dist/vueDatePick.css';
export default { 
  components: {DatePick},
   data(){
     
  return{ 
      error:'',
    name:'',
    date: '2021-01-01'
  };
  },
  methods:{
    
    checkForm:function(e) {
     if(this.name=='')
    this.error="please fill up your name field";
    
e.preventDefault();
    }
  }
}
</script>
<style scoped>
input,select {
  margin-left: 10px;
}
</style>