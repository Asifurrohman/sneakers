<template>
    <div class="flex items-center gap-4 mb-4">
        <font-awesome-icon icon="fa-solid fa-arrow-left" @click="() => closeDrawer()" class="opacity-30 cursor-pointer hover:opacity-100 transition-all"/>
        <h2 class="text-2xl font-bold">My Cart</h2>
    </div>
</template>

<script setup>
import { inject } from 'vue'

const { closeDrawer } = inject('cart')
</script>

<style scoped>

</style>