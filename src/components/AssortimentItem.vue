<template>
  <div class="">
    <img class="h-1/3" :src="item.image" />
    <span class="font-thin leading-none m-2 w-9/12"> {{ item.title }} </span>
    <button
      class="bg-light-100 font-thin w-25 rounded-2xl border float-right"
      @click="plus()"
    >
      {{ (item.count == null ? "Купить" : "Добавить") + ` за ${item.price}$` }}
    </button>
    <button
      class="bg-light-100 font-thin w-25 rounded-2xl border float-right"
      @click="deleteItem()"
      v-show="item.count != null"
    >
      Удалить
    </button>
  </div>
</template>
<script>
export default {
  props: ["item"],
  methods: {
    plus: function () {
      this.$emit("add-item", this.item.id);
    },
    deleteItem: function () {
      this.$emit("delete-item", this.item.id);
    },
  },
};
</script>