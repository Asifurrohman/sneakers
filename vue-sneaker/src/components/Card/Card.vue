<template>
    <div class="relative bg-white border border-slate-100 p-8 rounded-3xl cursor-pointer hover:-translate-y-2 hover:shadow-xl transition">
        <img @click="onClickFavourite" :src="!isFavourite ? '/img/like-1.svg' : '/img/like-2.svg'" alt="Favourite" class="absolute top-8 left-8">
        <img :src="imageUrl" alt="Sneaker">
        <p class="mt-2">
            {{ title }}
        </p>
        <div class="flex justify-between mt-5">
            <div class="flex flex-col">
                <span class="text-slate-400">Price:</span>
                <span class="font-bold">Rp {{ price }}</span>
            </div>
            <img @click="onClickAdd" :src="!isAdded ? '/img/plus.svg' : '/img/checked.svg'" alt="Add">
        </div>
    </div>
</template>

<script setup>

defineProps({
    id: Number,
    imageUrl: String,
    title: String,
    price: Number,
    isFavourite: Boolean,
    isAdded: Boolean,
    onClickFavourite: Function,
    onClickAdd: Function
})
</script>

<style scoped>

</style>