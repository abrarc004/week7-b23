<template>
  <div>
   <h1>Add page</h1>
   <div class="container">
   <div class="card bg-light p-3">
   <div class="alert alert-success" role="alert" v-if="success">
  Hotel successfully added
</div>
   <input type="text" name="name" placeholder="Enter hotel name" class="form-control mb-3" v-model="name">
   <input type="number" name="price" placeholder="Enter hotel price" class="form-control mb-3" v-model="price">
   <input type="text" name="location" placeholder="Enter hotel location" class="form-control mb-3" v-model="location">
   <input type="text" name="type" placeholder="Enter hotel type" class="form-control mb-3" v-model="type">
   <input type="text" name="imgurl" placeholder="Enter hotel image url" class="form-control mb-3" v-model="imgurl">
   <button class="btn btn-primary" v-on:click="addPressed" v-bind:disabled="loading"><i class="fas fa-spinner fa-spin" v-if="loading"></i><span v-if="!loading">Add new hotel</span></button>
   </div>
   </div>
  </div>
</template>

<script>

export default {
  name: 'Add',
  data (){
 return {
 name:'',
 price:'',
 location:'',
 type:'',
 imgurl:'',
 loading:false,
 success:false
 }
  },
  methods: {
  addPressed:function(){
let url = 'https://api.sheety.co/14e54678109837e42cb17c0e97377090/hotels/sheet1';
  let body = {
    sheet1: {
     name:this.name,
     location:this.location,
     price:this.price,
     type:this.type,
     imgurl:this.imgurl
    }
  }
  this.loading = true;
  this.success = false
  fetch(url, {
    method: 'POST',
    body: JSON.stringify(body),
    headers:{"Content-Type":"application/json"}
  })
  .then((response) => response.json())
  .then(json => {
  this.loading = false
  this.success = true
    // Do something with object
    console.log(json.sheet1);
    this.name ="";
    this.price ="";
    this.location="";
    this.type="";
    this.imgurl="";

  });
  }
  }
 
}
</script>
