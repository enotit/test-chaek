<template>
  <div
    id="ShoppingCart"
    class="bg-gray-200 h-128 w-64 rounded-2xl border border-gray-300"
  >
    <div class="text-center w-full">
      <span class="font-extrabold text-xl text-gray-700"> Корзина</span>
    </div>
    <div class="h-10/12 overflow-y-scroll overflow-x-hidden">
      <div v-if="items != null">
        <CartItem
          @reduce-item="reduceItem"
          @add-item="addItem"
          v-for="i of items.filter(x => x.count != null)"
          :key="i"
          :item="i"
        />
      </div>
    </div>
    <div class="inline-flex mt-2">
      <div class="m-2">
        <span class="font-extrabold"> Итого: </span>
        <span class="font-thin opacity-70">{{ salamary }}р. </span>
      </div>
      <button class="bg-light-100 font-thin w-25 rounded-2xl border" @click="msg()">
        Оплатить
      </button>
    </div>
  </div>
</template>

<script>
import CartItem from "@/components/CartItem.vue";
export default {
  props: ["items"],
  components: {
    CartItem,
  },
  methods: {
    reduceItem(id) {
      let temp = this.items.find((x) => x.id == id);
      if (temp.count != null) {
        if (temp.count == 1) temp.count = null;
        else temp.count -= 1;
      }
    },
    addItem(id) {
      let temp = this.items.find((x) => x.id == id);
      temp.count = temp.count == null ? 1 : temp.count + 1;
    },
    msg() {
        alert('Это вымышленный магазин, что оплатить хочешь?')
    }
  },
  computed: {
    salamary: function () {
      let s = 0;
      this.items.forEach((item) => {
        if (item.count != null) s += item.price * item.count;
      });
      return s.toFixed(2);
    },
  },
};
</script>
