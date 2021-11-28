<template>
  
   <form action="form" @submit.prevent="add()">
    <div class="">
    <div class="mt-5 row">
	<div class="col-md-1">
		
	</div>
	<div class="col-md-3 ">
		<div class="row">
			<div class="col-md-3">
				
			</div>
			<div class="col-md-9">
  <div class="d-flex flex-column mb-3 justify-content-center text-center">
  <span v-if="steps.basics==1"> <div class="p-2 mt-1 divborder"><router-link :to="{ path: '/basic'+this.$route.params.id }" style="text-decoration:none;">Basic</router-link></div></span>
  <span v-else> <div class=" p-2 mt-1 divborder"><router-link :to="{ path: '/basic'+this.$route.params.id } " style="text-decoration:none;">Basic</router-link></div></span>
  <span v-if="steps.description==1"> <div class="p-2 mt-1 divborder"><router-link :to="{ path: '/description'+this.$route.params.id }" style="text-decoration:none;">Description</router-link></div></span>
  <span v-else> <div class=" p-2 mt-1 divborder"><router-link :to="{ path: '/description'+this.$route.params.id }" style="text-decoration:none;">Description</router-link></div></span>
  <div class="ab p-2 mt-1 divborder">Location</div>
  <span v-if="steps.amenity==1"><div class="p-2 mt-1 divborder"><router-link :to="{ path: '/amenities'+this.$route.params.id }" style="text-decoration:none;">Amenities</router-link></div></span>
  <span v-else><div class=" p-2 mt-1 divborder"><router-link :to="{ path: '/amenities'+this.$route.params.id }" style="text-decoration:none;">Amenities</router-link></div></span>
  <span v-if="steps.photos==1"> <div class="p-2 mt-1 divborder"><router-link :to="{ path: '/photo'+this.$route.params.id }" style="text-decoration:none;">Photo</router-link></div> </span>
  <span v-else> <div class=" p-2 mt-1 divborder"><router-link :to="{ path: '/photo'+this.$route.params.id }" style="text-decoration:none;">Photo</router-link></div> </span>
  <span  v-if="steps.pricing==1"><div class="p-2 mt-1 divborder"><router-link :to="{ path: '/price'+this.$route.params.id }" style="text-decoration:none;">Pricing</router-link></div></span>
  <span v-else> <div class=" p-2 mt-1 divborder"><router-link :to="{ path: '/price'+this.$route.params.id }" style="text-decoration:none;">Pricing</router-link></div> </span>
  <span v-if="steps.booking==1"> <div class="p-2 mt-1 divborder"><router-link :to="{ path: '/booking'+this.$route.params.id }" style="text-decoration:none;">Booking</router-link></div> </span>
  <span v-else> <div class=" p-2 mt-1 divborder"><router-link :to="{ path: '/booking'+this.$route.params.id }" style="text-decoration:none;">Booking</router-link></div> </span>
  
  
</div>
</div>			
</div>
	
</div>
<div class="col-md-6 border pb-3 pl-2 colh">
  <div class="border d-flex flex-row row" style="height:408px;">
    <div class="backgrnd d-flex align-items-start">
      <h4>Location</h4>
    </div>
    <div class="mt-3">
   <label class="form-label" for="listingName">
     <h6>Country<span class="text-danger">*</span></h6>
   </label>
    <select id="inputState" class="form-select" v-model="country" required>
     <option  v-for="(countrylist,index) in countries" 
      :key="countrylist.id" :value="index">{{countrylist}}</option> 
    
    </select>
    </div>
    <div class="mt-3">
   <label class="form-label" for="listingName">
     <h6>Address Line 1 <span class="text-danger">*</span></h6>
   </label>
   <input type="text" class="form-control" id="listingName" placeholder="Entire home/apt in Dhaka" v-model="address_line_1" required>
    </div>
   
    <div class="d-flex flex-row">
    <div class="col-md-5">
    <div>
   <label class="form-label" for="listingName">
     <h6>Address Line 2<span class="text-danger">*</span></h6>
   </label>
   <input type="text" class="form-control" id="listingName" placeholder="Entire home/apt in Dhaka" v-model="address_line_2" required>
    </div>
    </div>
    <div class="col-md-1">
    </div>
    <div class="col-md-6">
    <div>
   <label class="form-label" for="listingName">
     <h6>City / Town / District <span class="text-danger">*</span></h6>
   </label>
   <input type="text" class="form-control" id="listingName" placeholder="Entire home/apt in Dhaka" v-model="city" required>
    </div>
    </div>      
    </div>

<div class="d-flex flex-row">
    <div class="col-md-5">
    <div>
   <label class="form-label" for="listingName">
     <h6>State / Province / County / Region<span class="text-danger">*</span></h6>
   </label>
   <input type="text" class="form-control" id="listingName" placeholder="Entire home/apt in Dhaka" v-model="state" required>
    </div>
    </div>
    <div class="col-md-1">
    </div>
    <div class="col-md-6">
    <div>
    
   <label class="form-label" for="listingName">
     <h6>ZIP / Postal Code<span class="text-danger">*</span></h6>
   </label>
   <input type="text" class="form-control" id="listingName" placeholder="Entire home/apt in Dhaka" v-model="postal_code" required>
    </div>
    </div>      
    </div>
  </div>
  <div class="d-flex justify-content-between mt-3">
    <div>
   <router-link :to="{ path: '/description'+this.$route.params.id }" class="btn btn-primary mt-4">Back</router-link>
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
</template>
<script>

import axios from "axios";
export default {
  name: "user",
  data() {
    return {
      country:'',
      countries:'',
      address_line_1:'',
      address_line_2:'',
      latitude:'15.486476',
      longitude:'73.809443',
      city:'',
      state:'',
      postal_code:'',
      
      step:'',
      steps:'',

      loading: false,     
    };
  },
  mounted(){ 
 this.view();
    
 },
methods: { 
view() {
      let user = JSON.parse(localStorage.getItem("user"));
      axios
        .get(
          "https://vrent.techvill.org/vrentapi/api/listing/" +
            this.$route.params.id +
            "/location",
          {
            headers: { Authorization: "Bearer " + user.token },
          }
        )
        .then((res) => {
          this.countries=res.data.data.country,
          this.country=res.data.data.address.country,
          this.address_line_1=res.data.data.address.address_line_1,
          this.address_line_2=res.data.data.address.address_line_2,
          this.city=res.data.data.address.city,
          this.state=res.data.data.address.state,
          this.postal_code=res.data.data.address.postal_code,
          this.step=res.data.data.step,
          this.steps=res.data.data.steps;
          console.log(res.data);
              
        });
    },

    add() {
      this.loading = true;
      let user = JSON.parse(localStorage.getItem("user"));
      axios
        .post(
          "https://vrent.techvill.org/vrentapi/api/listing/" +
            this.$route.params.id +
            "/location",
          
          { 
           latitude:this.latitude,
           longitude:this.longitude,
           country:this.country,
           address_line_1:this.address_line_1,
           address_line_2:this.address_line_2,
           city:this.city,
           state:this.state,
           postal_code:this.postal_code
          },
          {
            headers: { Authorization: "Bearer " + user.token },
          }
        )
        .then((res) => {
            this.loading = false;
          this.$router.push(`/amenities${res.data.data.id}`);            
        }).catch((res) => {
          res.data
          this.loading = false         
        });
    },


},

}
</script>
<style scoped>
.colh{
    flex: 0 0 auto;
    width: 50%;
    height: 500px;
    background: white;
}
.divborder{ 
border:1px solid black;
}
.backgrnd{ 
background-color: #EEEEEE;
padding: 5px;
padding-left: 14px;
}
.RoomsandBeds:hover{ 
background-color: #6C757D;
color:white;
}
.Listings:hover{ 
background-color: #6C757D;
color:white;
}
.bg{ 
background-color: #DFDBD2;
border: 1px solid gray;
}
.ab{
background-color:#74992e;
}
.bg:a{ 
color:#353935;
}
.bg a:hover{
text-decoration:none;
color: white;
}
.bg:hover{
background-color: #6C757D;
color: white;
font-size: 18px;
font-weight: bold;
}
.bgbasic{
background-color: rgb(199, 183, 183);
}
.bgdescription{
background-color: rgb(199, 183, 183);
}
</style>