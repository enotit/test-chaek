<template>
  <div class="w-full inline-block flex">
    <div class="font-semibold leading-tight">
      <span> {{ category.category }} </span>
    </div>

    <div class="">
      <input type="checkbox" @click="click()" />
    </div>
  </div>
</template>
<script>
export default {
  props: ["category"],
  methods: {
    click: function () {
      this.$emit("click-checkbox", this.category.category);
    },
  },
};
</script>