<template>
  <div class="cart">
    <h2>Cart</h2>
    <ul>
      <li v-for="(item, index) in cart" :key="index">
        {{ item.name }} - Quantity: {{ item.quantity }} - Total: ₱{{ item.total }}
        <button @click="removeFromCart(index)">Remove</button>
        <input type="number" min="1" v-model="item.quantity" @change="updateQuantity(item, index)">
      </li>
    </ul>
    <p>Total: ₱{{ total }}</p>
  </div>
</template>

<script>
export default {
  props: ['cart'],
  computed: {
    total() {
      return this.cart.reduce((acc, item) => acc + item.total, 0);
    }
  },
  methods: {
    removeFromCart(index) {
      this.$emit('remove-from-cart', index);
    },
    updateQuantity(item, index) {
      this.$emit('update-quantity', { item, index });
    }
  }
}
</script>

<style scoped>
/* Scoped styles */
.cart{
  border: 1px solid #000000;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  background-color: #f9f9f9;
}
</style>
