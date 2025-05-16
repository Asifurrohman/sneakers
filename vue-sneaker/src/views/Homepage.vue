<template>
    <!-- <Drawer></Drawer> -->
    <div class="my-10">
        <div class="flex justify-between items-center">
            <h2 class="text-3xl font-bold">
                All Sneakers
            </h2>
            
            <div class="flex gap-4">
                <select @change="onChangeSelect" class="py-2 px-4 border border-slate-200 focus:border-slate-400 outline-none rounded-md">
                    <option value="name">By Name</option>
                    <option value="price">By Price (Cheaper)</option>
                    <option value="-price">By Price (More Expensive)</option>
                </select>
                
                <div class="relative">
                    <font-awesome-icon icon="fa-solid fa-magnifying-glass" class="absolute left-4 top-3" />
                    <input @input="onChangeSearchInput" type="text" class="border border-slate-200 focus:border-slate-400 rounded-md py-1.5 pl-10 pr-4 outline-none" placeholder="Search...">
                </div>
            </div>
        </div>
        
        <CardList :items="items" @addToFavourite="addToFavourite"></CardList>
        
    </div>
</template>

<!-- terakhir video tutorial di waktu 04:31:26 -->

<script setup>
import CardList from '@/components/Card/CardList.vue'
import Drawer from '@/components/Drawer/Drawer.vue'

import { ref, onMounted, watch, reactive, provide } from 'vue'
import axios from 'axios'

const items = ref([])
const favourites = ref([])

const filters = reactive({
    sortBy: 'title',
    searchQuery: ''
})

const onChangeSelect = (event) => {
    filters.sortBy = event.target.value
    console.log(filters.sortBy)
}

const onChangeSearchInput = (event) => {
    filters.searchQuery = event.target.value
    console.log(filters.searchQuery)
}

const addToFavourite = async(item) => {
    item.isFavourite = !item.isFavourite
    console.log(item)
}

const fetchItems = async() => {
    try{
        const params = {
            sortBy: filters.sortBy,
        }

        if(filters.searchQuery){
            params.title = `*${filters.searchQuery}*`
        }

        const { data } = await axios.get(`https://70e0dec5c69ca79f.mokky.dev/items`, { params })
        items.value = data.map((obj) => ({
            ...obj,
            isFavourite: false,
            isAdded: false
        }))

    } catch(err){
        console.error(err)
    }
}

const fetchFavourites = async() => {
    try{
        const { data: favourites } = await axios.get(`https://70e0dec5c69ca79f.mokky.dev/favourites`)
        items.value = items.value.map(item => {
            const favourite = favourites.find(favourite => favourite.parentId === item.id)

            if(!favourite){
                return item
            }

            return {
                ...item,
                isFavourite: true,
                favouriteId: favourite.id
            }
        })

        console.log(items.value)
    } catch(err){
        console.error(err)
    }
}

onMounted(async() => {
    await fetchItems()
    await fetchFavourites()
})

watch(filters, fetchItems)

provide('addToFavourite', addToFavourite)
</script>

<style scoped>

</style>