<template>
 <div class="container">
 <form id="app" @submit="checkForm">
  
 <p class="text-info">{{ error }}</p>

  <p>
    <label for="name">New Product Name: </label>
    <input type="text" name="name" id="name" v-model="name">
  </p>

  <p>
    <input type="submit" value="Submit">  
  </p>

</form>
 </div>
</template>
<script>
export default { 
   data(){
  return{ 
      error:'',
    name:''
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