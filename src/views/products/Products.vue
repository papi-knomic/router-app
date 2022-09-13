<template lang="">
    <h1>Products</h1>
    <div v-for="product in products" :key="product.id">
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


<style lang="">
    
</style>