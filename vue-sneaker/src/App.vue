<template>
    <div class="bg-white font-inter">
        <!-- <Drawer v-if="drawerOpen"></Drawer> -->
        <!-- <Header @openDrawer="openDrawer"></Header> -->
        <div>
            <RouterView></RouterView>
        </div>
    </div>
</template>

<script setup>
import { ref, provide } from 'vue'
import { RouterLink, RouterView } from 'vue-router'
import Header from './components/Header.vue'
import Drawer from './components/Drawer/Drawer.vue'

// const drawerOpen = ref(false)

// const closeDrawer = () => {
//     drawerOpen.value = false
// }

// const openDrawer = () => {
//     drawerOpen.value = true
// }

// provide('cartActions', {
//     closeDrawer,
//     openDrawer
// })
</script>

<style scoped>

</style>
