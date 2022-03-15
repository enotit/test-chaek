<template>
  <div class="float-left z-2">
    <CategoryFilter class="" :categories="categories" />
  </div>
  <div class="float-right z-2">
    <ShoppingCart class="" v-if="items != null" :items="items" />
    <img src="./assets/loading.gif" alt="" v-else />
  </div>
  <div class="absolute ml-90">
    <AssortimentProducts :items="items" :categories="categories" />
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
      categories: null,
    };
  },
  components: {
    CategoryFilter,
    ShoppingCart,
    AssortimentProducts,
  },
  methods: {
    checkCategories: function () {
      if (this.items == null) return;
      let temp = [];
      this.items.forEach((i) => {
        if (temp.find((x) => x.category == i.category) == null)
          temp.push({ category: i.category, selected: false });
      });
      this.categories = temp;
    },
  },
  beforeCreate() {
    axios
      .get("https://fakestoreapi.com/products")
      .then((response) => {
        this.items = response.data;
        let temp = [];
        this.items.forEach((i) => {
          if (temp.find((x) => x.category == i.category) == null)
            temp.push({ category: i.category, selected: false });
        });
        this.categories = temp;
      })
      .catch((error) => {
        alert(error);
      });
  },
  computed: {},
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
  outline: 0; outline-offset: 0;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>