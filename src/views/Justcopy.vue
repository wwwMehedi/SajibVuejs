<template>
  
   <form action="form" @submit.prevent="add()">
    <div class="container">
    <div class="mt-5 row">
	<div class="col-md-1">
		
	</div>
	<div class="col-md-3 ">
		<div class="row">
			<div class="col-md-3">
				
			</div>
			<div class="col-md-9">
  <div class="d-flex flex-column mb-3 justify-content-center text-center">
 <span v-if="steps.basics==1">  <div class=" p-2  mt-1" style="border:1px solid black;"> <router-link :to="{ path: '/basic'+this.$route.params.id }" style="text-decoration:none;">Basic</router-link>
  </div></span>
 <span v-else> <div class="bgbasic p-2  mt-1"><router-link :to="{ path: '/basic'+this.$route.params.id }" style="text-decoration:none;">Basic</router-link></div></span>
 <span v-if="steps.description==1"><div class="p-2 mt-1" style="border:1px solid black;"><router-link :to="{ path: '/description'+this.$route.params.id }" style="text-decoration:none;">Description</router-link></div></span>
 <span v-else><div class="bgbasic p-2 mt-1"><router-link :to="{ path: '/description'+this.$route.params.id }" style="text-decoration:none;">Description</router-link></div></span> 
 <span v-if="steps.location==1"><div class="p-2 mt-1" style="border:1px solid black;"><router-link :to="{ path: '/location'+this.$route.params.id }" style="text-decoration:none;">Location</router-link></div></span>
 <span v-else><div class="bgbasic p-2 mt-1" style="border:1px solid black;"><router-link :to="{ path: '/location'+this.$route.params.id }" style="text-decoration:none;">Location</router-link></div></span>
  
  <div class="ab p-2 mt-1">Amenities</div>
  <span v-if="steps.photos==1"> <div class="p-2 mt-1" style="border:1px solid black;"><router-link :to="{ path: '/photo'+this.$route.params.id }" style="text-decoration:none;">Photos</router-link></div> </span>
  <span v-else> <div class="bgbasic p-2 mt-1"><router-link :to="{ path: '/photo'+this.$route.params.id }" style="text-decoration:none;">Photos</router-link></div> </span>
  <span  v-if="steps.pricing==1"><div class=" p-2 mt-1"  style="border:1px solid black;"><router-link :to="{ path: '/price'+this.$route.params.id }" style="text-decoration:none;">Pricing</router-link></div></span>
  <span v-else> <div class="bgbasic p-2 mt-1"><router-link :to="{ path: '/price'+this.$route.params.id }" style="text-decoration:none;">Pricing</router-link></div> </span>

  <span v-if="steps.booking==1"> <div class="p-2 mt-1" style="border:1px solid black;"><router-link :to="{ path: '/booking'+this.$route.params.id }" style="text-decoration:none;">Booking</router-link></div> </span>
  <span v-else> <div class="bgbasic p-2 mt-1"><router-link :to="{ path: '/booking'+this.$route.params.id }" style="text-decoration:none;">Booking</router-link></div> </span>
  
 
</div>
</div>
</div>
</div>
<div class="col-md-6  pb-3 pl-2">
  <div class="border d-flex flex-row row">
    <div class="backgrnd d-flex justify-content-between">
    <div> <h4>Common Amenities</h4></div>
    </div>
    <div class="row" style="height:700px;">

    <div class="mt-3">
    
 <div class="form-check" v-for="am in amenities" :key="am.id">
 <div v-if="am.type_id==1">

  <input class="form-check-input" type="checkbox" :value="am.id" v-model="amen" id="flexCheckDefault" name="amenities[]" data-saving="1">
  <label class="form-check-label" for="flexCheckDefault">
    {{am.title}}
  </label>

</div>
</div>

</div>
</div>

</div>
  <div class="d-flex justify-content-between mt-3 mb-5">
    <div>
     <router-link :to="{ path: '/location'+this.$route.params.id }" class="btn btn-primary mt-4">Back</router-link>
    </div>
    <div>

     <button type="submit" class="btn btn-primary mt-4" :disabled="loading">
<span v-if="loading" class="spinner-border spinner-border-sm" role="status" aria-hidden="true"></span> Next</button>
   
    </div>
  </div>
</div>

<div class="col-md-2">
</div>
	
</div>

</div>
    

</form>
