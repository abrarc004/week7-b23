<template>
  <div class="home">
   <h1>Home page</h1>
   <button class="btn btn-secondary" v-on:click="addPressed">Add a new hotel</button>
  <table class="table table-bordered table-striped">
 <thead>
 <tr>
<th></th>
<th>Name</th>
<th>Actions</th>
 </tr>
</thead>
<tbody>
 <tr  v-for="hotel in hotels" :key="hotel.id">
 <td><img v-bind:src="hotel.imgurl" class="img-fluid"></td>
 <td>{{hotel.name}}</td>
 <td>
 <button class="btn btn-success" v-on:click="viewPressed(hotel)">View</button>
 <button class="btn btn-primary"  v-on:click="editPressed(hotel)">Edit</button>
 <button class="btn btn-danger">Delete</button>
 </td>
  </tr>
 </tbody>
</table>  
  </div>

</template>

<script>

export default {
  name: 'Home',
  mounted (){
let url = 'https://api.sheety.co/14e54678109837e42cb17c0e97377090/hotels/sheet1';
fetch(url)
.then((response) => response.json())
.then(json => {
  // Do something with the data
this.hotels =json.sheet1;
});
  },
  data (){
  return {
  hotels:[]

  }
  },
  methods: {
 viewPressed(hotel){
  this.$router.push('detail/'+hotel.id)
  },
  editPressed(hotel){
  this.$router.push('edit/'+hotel.id)
  },
  addPressed(){
  this.$router.push('add')
  }

  }
 
}
</script>
