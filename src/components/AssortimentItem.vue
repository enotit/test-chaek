<template>
    <div class="bg-light-400 h-44 w-12 rounded-b-lg"> 
        <span> {{item.title}} </span>
        <!-- <img :src="item.image"> -->
    </div>
</template>
<script>
export default {
    props: ["item"]
}
</script>