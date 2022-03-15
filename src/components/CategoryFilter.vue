<template>
  <div
    id="CategoryFilter"
    class="bg-gray-200 h-110 w-64 rounded-r-3xl border border-gray-300"
  >
    <div class="text-center w-full">
      <span class="font-extrabold text-xl text-gray-700"> Фильтр </span>
    </div>
    <div
      v-if="categories != null"
      class="h-10/12 overflow-x-hidden overflow-y-scroll"
    >
      <div v-for="category in categories" :key="category">
        <div class="w-full mt-2 ml-3 inline-block">
          <div class="font-semibold leading-tight inline">
            <span> {{ category.category }} </span>
          </div>

          <div class="inline float-right mr-5">
            <input
              type="checkbox"
              @click="clickCheckbox(category.category)"
              v-model="category.selected"
            />
          </div>
        </div>
      </div>
    </div>
    <div v-else>Загрузка...</div>
    <div v-if="categories != null">
      <button
        class="bg-light-100 font-thin w-25 rounded-2xl border"
        @click="change_all(false)"
        v-show="categories.find((x) => x.selected == true) != null"
      >
        Сбросить всё
      </button>
      <button
        class="bg-light-100 font-thin w-25 rounded-2xl border float-right"
        @click="change_all(true)"
        v-show="categories.find((x) => x.selected == false) != null"
      >
        Выбрать всё
      </button>
    </div>
  </div>
</template>
<script>
// import LineCategory from "@/components/LineCategory";
export default {
  props: ["categories"],
  components: {
    // LineCategory,
  },
  methods: {
    clickCheckbox: function (category) {
      let temp = this.categories.find((c) => c.category == category);
      temp.selected = !temp.selected;
    },
    change_all: function (switcher) {
      this.categories.forEach((category) => {
        category.selected = switcher;
      });
    },
  },
  computed: {},
};
</script>
