<template>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 mt-10">
        <Card v-for="item in items" :key="item.id" :id="item.id" :title="item.title" :price="item.price" :imageUrl="item.imageUrl" :onClickFavourite="() => emit('addToFavourite', item)" :onClickAdd="() => emit('addToCart', item)" :isFavourite="item.isFavourite" :isAdded="item.isAdded"></Card>
    </div>
</template>

<script setup>
import Card from './Card.vue'

defineProps({
    items: Array
})

const emit = defineEmits(
    ['addToFavourite', 'addToCart']
)
</script>

<style scoped>

</style>