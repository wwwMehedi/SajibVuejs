<template>
    <div class="container">
    <div class="row mt-5">
    </div>
    <div class="row mt-5">
    <div class="col-md-2">
    </div>
    <div class="col-md-8 mt-5 pb-5" style="box-shadow: 0px 0px 2px 0px gray;" >
  <div class="row text-center mt-5">
  <h1>List Your Space</h1>
  <p class="pt">Vrent Lets you make money renting out your place.</p>
  </div>
  <form name="form" @submit.prevent="add()">
      <div class="row">
      <div class="col-md-6">
       <label for="inputState" class="form-label ">Home Type</label>
    <select id="inputState" class="form-select" v-model="property_type">
    
      <option  v-for="(view,index) in show" :key="view.id" :value="index">{{view}}</option>
       
    </select>

      </div>
        <div class="col-md-6">
       <label for="inputState2" class="form-label">Room Type</label>
    <select id="inputState2" class="form-select" v-model="space_type">
      <option selected v-for="(room,index) in rooms" :key="room.id" :value="index">{{room}}</option>
    </select>

      </div>
      </div>
    <div class="row">
      <div class="col-md-6">
       <label for="inputState" class="form-label">Acomodates</label>
    <select id="inputState" class="form-select" v-model="accommodates" required>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
    </select>       
      </div>
      
        <div class="col-md-6">
       <label for="inputState" class="form-label">city</label>
    <input type="text" class="form-control" v-model="map_address">
      </div>

      </div>
      <div class="d-flex justify-content-end">
      <button type="submit" class="btn btn-primary mt-4" :disabled="loading"><span
                  v-if="loading"
                  class="spinner-border spinner-border-sm"
                  role="status"
                  aria-hidden="true"
                ></span>Next</button>
      </div>
      
 </form>
    </div>
  
    <div class="col-md-2">
    </div>

    </div>
    
    </div>
</template>

<script>
import axios from "axios";
//import axios from "axios";
export default{ 
name:"user",
data(){ 
return{ 
show:"",
rooms:"",
accommodates:"",
map_address:"",
property_type:"",
space_type:"",
dummy:"",
loading:false,
};
},
mounted() { 
  this.view();
 
},
 methods: {
 view() {
      let user = JSON.parse(localStorage.getItem("user"));
      axios
        .get("https://vrent.techvill.org/vrentapi/api/property/create", {
          headers: {Authorization:"Bearer "+ user.token },
        })
        .then((res) => {
          this.show = res.data.data.propertyType;
          this.rooms = res.data.data.spaceType;
          
        });
    },

    add(){ 
      this.loading=true;
      let user=JSON.parse(localStorage.getItem("user"));
      axios.post("https://vrent.techvill.org/vrentapi/api/property/create",
      { 
        property_type:this.property_type,
        space_type:this.space_type,
        accommodates:this.accommodates,
        map_address:this.map_address,
      },

      { 
        headers:{Authorization: "Bearer "+user.token }
      }
      
      ).then((res)=>{ 
        this.loading=false,
        res.data
       console.log(res.data);
       this.$router.push(`/basic${res.data.data.property.id}`);
    
      }).catch((res) => {
          res.data
          this.loading = false         
        });
      
    }

  },




};
 
</script>

<style scoped>
label {
  font-size: 22px;
}
.pt{ 
font-size: 22px;
color: rgb(185, 122, 122);
}
</style>
