<template lang="">
    <h1>Products</h1>
    <div v-if="products">
      <div v-for="product in products" :key="product.id" class="product">
        <router-link :to="{name: 'productsDetails', params: { id: product.id} }"><h2>{{product.name}}</h2></router-link>
    </div>
    </div>
    <div v-else>
      <p>Loading Products....</p>
    </div>
    
</template>


<script>

export default {
    data () {
    return {
      products: null
    }
  },
  mounted () {
    fetch('http://127.0.0.1:8000/api/products')
      .then(res => res.json())
      .then( data => this.products = data.data)
      .catch( error => console.log(error.message))
  }
}
</script>


<style>
  .product h2{
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;
  } 
  
  .product h2:hover{
    background: #ddd;
  }
  .product a{
    text-decoration: none;
  }
</style>