<template>
  <div class="">
    <ShoppingCart/>
  </div>
</template>

<script>
import ShoppingCart from "@/components/ShoppingCart"

export default {
  name: 'App',
  components: {
    ShoppingCart
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100;0,300;0,600;1,300&display=swap');
  html, body{
    background-color: rgb(243, 244, 246);
    outline:none;
    font-family: 'Montserrat', sans-serif;
  }
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0; /* <-- Apparently some margin are still there even though it's hidden */
}
</style>