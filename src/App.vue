<template>
  <div class="">
      <CategoryFilter class="" :categories="categories" />
    </div>
  <div class="">
    <ShoppingCart class="" v-if="items != null" :items="items" />
    <img src="./assets/loading.gif" alt="" v-else>
  </div>
  <div>
    <AssortimentProducts :items="items"/>
  </div>
  
</template>

<script>
import ShoppingCart from "@/components/ShoppingCart";
import CategoryFilter from "@/components/CategoryFilter";
import AssortimentProducts from "@/components/AssortimentProducts";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      items: null,
    };
  },
  components: {
    CategoryFilter,
    ShoppingCart,
    AssortimentProducts
  },
  beforeCreate() {
    axios
      .get("https://fakestoreapi.com/products")
      .then((response) => (this.items = response.data))
      .catch((error) => {
        alert(error);
      });
  },
  computed: {
    categories: function(){
      if (this.items == null) return null;
      let temp = [];
      this.items.forEach((i) => {
        if (temp.find(x=> x.category == i.category) == null)
          temp.push({category: i.category, selected: false});
      });
      return temp;
    }
  }
};
</script>

<style>
/* @import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100;0,300;0,600;1,300;&display=swap'); */
html,
body {
  background-color: rgb(243, 244, 246);
  outline: none;
  font-family: "Montserrat", sans-serif;
  user-select: none;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>