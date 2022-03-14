<template>
  <div
    id="ShoppingCart"
    class="bg-gray-200 h-110 w-64 rounded-2xl border border-gray-300"
  >
    <div class="text-center w-full">
      <span class="font-extrabold text-xl text-gray-700"> Фильтр </span>
    </div>
    <div v-if="categories != null">
      <div class="h-10/11 overflow-y-scroll m-5">
        <LineCategory
          @click-checkbox="clickCheckbox"
          v-for="category in categories"
          :key="category"
          :category="category"
        />
      </div>
    </div>
    <div v-else>Загрузка...</div>
  </div>
</template>
<script>
import LineCategory from "@/components/LineCategory";
export default {
  props: ["categories"],
  components: {
    LineCategory,
  },
  methods: {
    clickCheckbox: function (category) {
      let temp = this.categories.find((c) => c.category == category);
      temp.selected = !temp.selected;
    },
  },
  computed: {},
};
</script>
