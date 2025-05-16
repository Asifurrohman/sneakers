<template>
    <div class="bg-white font-inter">
        <Header></Header>
        <div class="mx-10">
            <RouterView></RouterView>
        </div>
    </div>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue'
</script>

<style scoped>

</style>
