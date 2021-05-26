<template>
  <div>
   <h1>{{hotel.name}}</h1>
   <p>Price: {{hotel.price}}</p>
   <p>Location : {{hotel.location}}</p>
  </div>
</template>

<script>

export default {
  name: 'Detail',
  mounted(){
  	let url = 'https://api.sheety.co/14e54678109837e42cb17c0e97377090/hotels/sheet1';
fetch(url)
.then((response) => response.json())
.then(json => {
  // Do something with the data
  this.hotels =json.sheet1;
});
  }
  data (){
  return{
name:'',
 price:'',
 location:'',
 type:'',
 imgurl:'',
  }
  },
 
}
</script>
