<template>
  <div class="m-4 flex flex-col">
    <span class="font-semibold leading-tight"> {{ item.title }} </span>
    <table>
      <tbody>
        <tr>
          <td>
            <span class="font-thin ml-3 opacity-70">{{ item.price }}р. </span>
          </td>
          <td rowspan="2">{{ salamary }}р.</td>
        </tr>
        <tr>
          <td>
            <div>
              <button class="text-2xl" @click="minus">-</button>
              <input
                type="number"
                name=""
                :value="count"
                id=""
                class="
                  w-8
                  text-gray-500/50
                  rounded-1xl
                  center
                  ml-1
                  mr-1
                  text-center
                "
              />
              <button class="text-2xl" @click="plus">+</button>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  <hr class="bg-black w-10/12 ml-5" />
</template>

<script>
export default {
  props: ["item"],
  data() {
    return {
      // count: 1,
    };
  },
  methods: {
    plus() {
      this.$emit("add-item", this.item.id);
    },
    minus() {
      this.$emit("reduce-item", this.item.id);
    },
  },
  computed: {
    count: function () {
      if (this.item.count == null) return 0;
      return this.item.count;
    },
    salamary: function () {
      let count = 0;
      if (this.item.count != null) count = this.item.count;
      let temp = count * this.item.price;
      return temp.toFixed(2);
    },
  },
};
</script>
