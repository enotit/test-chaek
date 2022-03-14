<template>
    <div class="bg-light-600 w-full h-44">
        <div v-for="i in items" :key="i">
            <AssortimentItem/>
        </div>
    </div>
</template>
<script>
import AssortimentItem from "./AssortimentItem.vue"
export default {
    props: ["items"],
    components: [
        AssortimentItem
    ]
}
</script>