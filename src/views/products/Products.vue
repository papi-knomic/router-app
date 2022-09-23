<template lang="">
    <h1>Products</h1>
    <div v-for="product in products" :key="product.id" class="product">
        <router-link :to="{name: 'productsDetails', params: { id: product.id} }"><h2>{{product.name}}</h2></router-link>
    </div>
    
</template>


<script>
import axios from 'axios';

export default {
    data () {
    return {
      products: null
    }
  },
  mounted () {
    axios
      .get('http://127.0.0.1:8000/api/products')
      .then(response => (this.products = response.data.data))
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