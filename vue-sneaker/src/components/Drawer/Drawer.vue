<template>
    <div @click="() => closeDrawer()" class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-50"></div>
    <div></div>
    <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
        <DrawerHead></DrawerHead>
        <CartItemList class="h-96 overflow-y-auto"></CartItemList>

        <div class="flex flex-col gap-4 mt-6">
            <div class="flex gap-2">
                <span>Total:</span>
                <div class="flex-1 border-b border-dashed"></div>
                <b>Rp 1500000</b>
            </div>
            <div class="flex gap-2">
                <span>Tax(12%):</span>
                <div class="flex-1 border-b border-dashed"></div>
                <b>Rp 180000</b>
            </div>
        </div>

        <button class="mt-4 bg-emerald-600 hover:bg-emerald-700 active:bg-emerald-800 disabled:bg-slate-300 text-white w-full rounded-xl py-2 cursor-pointer disabled:cursor-auto transition-all">
            Place an order
        </button>
    </div>
</template>

<script setup>
import { inject } from 'vue'

import DrawerHead from './DrawerHead.vue'
import CartItemList from '../Cart/CartItemList.vue'

const { closeDrawer } = inject('cart')
</script>

<style scoped>

</style>