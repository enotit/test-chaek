<template>
  <div class="" v-bind:items="items">
    <ShoppingCart
      v-bind:items="items"
    />
    <div v-for="i in items" :key="i" > {{ i.count }} </div>
  </div>
</template>

<script>
import ShoppingCart from "@/components/ShoppingCart"
import axios from "axios";

export default {
  name: 'App',
  data() {
    return{
      items: null// [{0: 1, 1:2, 3:4}, {1:2, 3:4}]
    };
  },
  components: {
    ShoppingCart
  },
  beforeCreate() {
     axios
      .get('https://fakestoreapi.com/products')
      .then(response => (this.items = response.data));
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100;0,300;0,600;1,300;800&display=swap');
html, body{
  background-color: rgb(243, 244, 246);
  outline:none;
  font-family: 'Montserrat', sans-serif;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

</style>