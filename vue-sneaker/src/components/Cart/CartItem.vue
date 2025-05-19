<template>
    <div class="flex items-center border border-slate-100 p-4 rounded-xl gap-4">
        <img :src="imageUrl" class="w-16 h-16 object-contain" :alt="title">
        <div class="flex flex-col">
            <p>{{ title }}</p>
            <div class="flex justify-between">
                <b>Rp {{ price }}</b>
                <span>
                    <font-awesome-icon icon="fa-solid fa-xmark" @click="emit('onClickRemove')" class="text-rose-600 border border-slate-100 p-2 rounded-lg cursor-pointer hover:bg-rose-100 transition-all"/>
                </span>
            </div>
        </div>
    </div>
</template>

<script setup>
defineProps({
    id: Number,
    title: String,
    imageUrl: String,
    price: Number
})

const emit = defineEmits([
    'onClickRemove'
])
</script>

<style scoped>

</style>