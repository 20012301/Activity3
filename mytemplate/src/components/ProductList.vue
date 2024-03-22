<template>
  <div class="product-list">
    <div v-for="product in products" :key="product.id" class="product">
      <h3>{{ product.name }}</h3>
      <p>Price: ₱{{ product.price }}</p>
      <button @click="addToCart(product)">Add to Cart</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['products'],
  methods: {
    addToCart(product) {
      this.$emit('add-to-cart', product);
    }
  }
}
</script>

<style scoped>
/* Scoped styles */
button {
padding: 10px 20px;
background-color: #007bff;
color: #fff;
border: none;
border-radius: 5px;
cursor: pointer;
}
.product-list{
  border: 1px solid #000000;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  background-color: #f9f9f9;
}
</style>