<template>
    <div id="ShoppingCart" class="bg-gray-200 h-128 w-64 rounded-2xl border border-gray-300" >
        <div class="text-center w-full">
            <span class="font-extrabold text-xl text-gray-700 "> Корзина</span>
        </div>
        <div class="h-10/12 overflow-y-scroll overflow-x-hidden">
            <CartItem 
                v-on:remove-item="removeItem"
                v-for="i of items" :key="i"
                v-bind:item="i"/>
        </div>
        <div class="inline-flex mt-2"> 
            <div class="m-2">
                <span class="font-extrabold"> Итого: </span>
                <span class="font-thin opacity-70">{{300}}р. </span>
            </div>
            <button class="bg-light-100 font-thin w-25 rounded-2xl border"> Оплатить </button>
        </div>
    </div>
</template>

<script>
import CartItem from '@/components/CartItem.vue'
export default {
    props: ['items'],
    components: {
        CartItem
    },
    methods: {
        removeItem(id){
            console.log(id)
        }
    }
}

</script>
