<template lang="">
    <h1> Product Detail Page</h1>
    <div v-if="product">
        <p>This is the product id {{ id }}</p>
        <p>This is the product price {{ product.price }}</p>
    </div>
    <div v-else>
        <p>It's loading.....</p>
    </div>
</template>

<script>

export default {
    props: ['id'],
    data() {
        return {
            product: null
        }
    },
    mounted () {
        fetch('http://127.0.0.1:8000/api/products/' + this.id)
      .then(res => res.json())
      .then( data => this.product = data.data)
      .catch( error => console.log(error.message))
  }
}
</script>

<style lang="">
    
</style>