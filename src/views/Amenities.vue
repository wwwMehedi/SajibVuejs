<template>
  
   <form action="form" @submit.prevent="add()">

    <div class="mt-5 row">
	<div class="col-md-1">
		
	</div>
	<div class="col-md-3 ">
		<div class="row">
			<div class="col-md-3">
				
			</div>
      <!--column div sart -->
<div class="col-md-9">
  <div class="d-flex flex-column mb-3 justify-content-center text-center">
  <span v-if="steps.basics==1"><div class="p-2 mt-1 divborder"> <router-link :to="{ path: '/basic'+this.$route.params.id }" style="text-decoration:none;">Basic</router-link>
  </div></span>
  <span v-else> <div class="bgbasic p-2 mt-1 divborder"><router-link :to="{ path: '/basic'+this.$route.params.id }" style="text-decoration:none;">Basic</router-link></div></span>
  <span v-if="steps.description==1"><div class="p-2 mt-1 divborder"><router-link :to="{ path: '/description'+this.$route.params.id }" style="text-decoration:none;">Description</router-link></div></span>
  <span v-else><div class="bgbasic p-2 mt-1 divborder"><router-link :to="{ path: '/description'+this.$route.params.id }" style="text-decoration:none;">Description</router-link></div></span> 
  <span v-if="steps.location==1"><div class="p-2 mt-1 divborder"><router-link :to="{ path: '/location'+this.$route.params.id }" style="text-decoration:none;">Location</router-link></div></span>
  <span v-else><div class="bgbasic p-2 mt-1 divborder"><router-link :to="{ path: '/location'+this.$route.params.id }" style="text-decoration:none;">Location</router-link></div></span>
  <div class="ab p-2 mt-1 divborder">Amenities</div>
  <span v-if="steps.photos==1"> <div class="p-2 mt-1 divborder"><router-link :to="{ path: '/photo'+this.$route.params.id }" style="text-decoration:none;">Photo</router-link></div> </span>
  <span v-else> <div class="bgbasic p-2 mt-1 divborder"><router-link :to="{ path: '/photo'+this.$route.params.id }" style="text-decoration:none;">Photo</router-link></div> </span>
  <span  v-if="steps.pricing==1"><div class=" p-2 mt-1 divborder"><router-link :to="{ path: '/price'+this.$route.params.id }" style="text-decoration:none;">Pricing</router-link></div></span>
  <span v-else> <div class="bgbasic p-2 mt-1 divborder"><router-link :to="{ path: '/price'+this.$route.params.id }" style="text-decoration:none;">Pricing</router-link></div> </span>
  <span v-if="steps.booking==1"> <div class="p-2 mt-1 divborder"><router-link :to="{ path: '/booking'+this.$route.params.id }" style="text-decoration:none;">Booking</router-link></div> </span>
  <span v-else> <div class="bgbasic p-2 mt-1 divborder"><router-link :to="{ path: '/booking'+this.$route.params.id }" style="text-decoration:none;">Booking</router-link></div> </span>
  </div>
</div>
<!--column div finish -->
</div>
</div>
<div class="col-md-6 border pb-3 pl-2 colh" >
  
   <div class="backgrnd d-flex align-items-start row">
      <h4>Amenities</h4>
    </div>

     <div class="h-75">
     <div class="" v-for="am in amenities" :key="am.id" >
              <div v-if="am.id<12">
                 <input class="" type="checkbox" :value="am.id" v-model="amen" id="flexCheckDefault" name="amenities[]" data-saving="1">
                   <label class="form-check-label" for="flexCheckDefault">
                     {{am.title}}
                    </label>
              </div>
        </div>
     </div>
         



      <div class="d-flex justify-content-between mt-3">
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




</form>
</template>
<script>

import axios from "axios";

export default {
  name: "user",
  data() {
    return {

      name:"",
      summary:"",
      step:'',
      steps:'',
      amenities:[],
      amen:[],
      loading:false,
     
    };
  },

  mounted(){ 
    this.view();
  },

 methods:{ 

view() {
  
      let user = JSON.parse(localStorage.getItem("user"));
      axios
        .get(
          "https://vrent.techvill.org/vrentapi/api/listing/" +
            this.$route.params.id +
            "/amenities ",
          {
            headers: { Authorization: "Bearer " + user.token },
          }
        )
        .then((res) =>{
         
            console.log(res.data);
            this.step=res.data.data.step;
            this.steps=res.data.data.steps;
            this.amenities=res.data.data.amenities;
            this.amen=res.data.data.property_amenities; 
             this.cd=false;       
        });
    },
    
    add() {
      this.loading = true;
      let user = JSON.parse(localStorage.getItem("user"));
      axios
        .post(
          "https://vrent.techvill.org/vrentapi/api/listing/" +
            this.$route.params.id +
            "/amenities",
          
          { 
           amenities:this.amen
          },

          {
            headers: { Authorization: "Bearer " + user.token },
          }
        
        )             
        .then((res) =>{
          this.loading = false;
            res.data
            this.$router.push(`/photo${res.data.data.id}`);
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

label{ 
  margin-left: 10px;
}
.height{ 
  height:700px;
}
.backgrnd{ 
background-color: #EEEEEE;
padding: 5px;
padding-left: 7px;
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
