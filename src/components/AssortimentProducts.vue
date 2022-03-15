<template>
  <div class="bg-dark-400 w-300 z-1 h-full">
    <div
    v-show="
          categories.find((x) => x.category == i.category).selected ||
          categories.find((x) => x.selected == true) == null
        "
      class="bg-light-400 h-75 w-40 rounded-3xl ml-5 block top-20"
      v-for="i in items"
      :key="i"
    >
      <AssortimentItem
      @add-item="addItem"
      @delete-item="deleteItem"
        :item="i"
      />
    </div>
  </div>
</template>
<script>
import AssortimentItem from "./AssortimentItem.vue";
export default {
  props: ["items", "categories"],
  components: {
    AssortimentItem,
  },
  methods: {
    addItem: function(id){
      let temp = this.items.find((x) => x.id == id);
      temp.count = temp.count == null ? 1 : temp.count + 1;
    },
    deleteItem: function(id){
      this.items.find((x) => x.id == id).count = null;
    }
  }
};
</script>