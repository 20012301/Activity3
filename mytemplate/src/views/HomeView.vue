<template>
  <div id="app">
    <h1>Vue Shopping Cart</h1>
    <ProductList :products="products" @add-to-cart="addToCart" />
    <ShoppingCart :cart="cart" @remove-from-cart="removeFromCart" @update-quantity="updateQuantity" />
    
    <button @click="handleLogout">Logout</button>
  </div>
</template>

<script>
import ProductList from '@/components/ProductList.vue';
import ShoppingCart from '@/components/ShoppingCart.vue';

export default {
  components: {
    ProductList,
    ShoppingCart
  },
  data() {
    return {
      products: [
        { id: 1, name: 'Polo Shirt', price: 350 },
        { id: 2, name: 'Pants', price: 150 },
        { id: 3, name: 'Jacket', price: 500 },
        { id: 4, name: 'Socks (Per Pack)', price: 100 },
        { id: 5, name: 'Shoes', price: 1000 },
        // Other product data...
      ],
      cart: []
    }
  },
  methods: {
    addToCart(product) {
      const index = this.cart.findIndex(item => item.id === product.id);
      if (index !== -1) {
        this.cart[index].quantity++;
        this.cart[index].total = this.cart[index].quantity * product.price;
      } else {
        this.cart.push({
          id: product.id,
          name: product.name,
          price: product.price,
          quantity: 1,
          total: product.price
        });
      }
    },
    removeFromCart(index) {
      this.cart.splice(index, 1);
    },
    updateQuantity({ item, index }) {
      item.total = item.quantity * item.price;
      this.cart[index] = item; // Directly assign item to the array element
    },
    handleLogout() {
      localStorage.removeItem('token')
      this.$router.push('/')
    },
  }
}
</script>

<style scoped>
/* Scoped styles */
button {
padding: 10px 20px;
background-color: red;
color: #fff;
border: none;
border-radius: 5px;
cursor: pointer;
}
</style>