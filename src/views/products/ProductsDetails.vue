<template lang="">
    <div>
        <h1> Product Detail Page</h1>
        <p>This is the job id {{ id }}</p>
        <p v-if="product">This is the product price {{ product.price }}</p>
    </div>
</template>

<script>
    import axios from 'axios';

export default {
    props: ['id'],
    data() {
        return {
            product: null
        }
    },
    mounted () {
    axios
      .get('http://127.0.0.1:8000/api/products/'+ this.id)
      .then(response => (this.product = response.data.data))
  }
}
</script>

<style lang="">
    
</style>