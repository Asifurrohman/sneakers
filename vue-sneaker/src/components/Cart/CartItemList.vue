<template>
    <div class="flex flex-col gap-4">
        <CartItem v-for="item in cart" :imageUrl="item.imageUrl" :key="item.id" :title="item.title" :price="item.price" @onClickRemove="() => removeFromCart(item)"></CartItem>
    </div>
</template>

<script setup>
import { inject } from 'vue'

import CartItem from './CartItem.vue'

const { cart, removeFromCart } = inject('cart')

</script>

<style scoped>

</style>