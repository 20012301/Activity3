<template>
    <div>
        <h1>Login Page to Vue Shopping Cart</h1>
        <button @click="handleClick">Login</button>
    </div>
</template>

<script>
export default {
    methods: {
        handleClick() {
            localStorage.setItem('token', '12345')
            this.$router.push({ name: 'home' })
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
</style>