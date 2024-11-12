<script setup>
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'
import { onMounted, ref, watch, reactive } from 'vue'
import axios from 'axios'

const items = ref([])
const favorites = ref([])

const filters = reactive({
  sortBy: 'title',
  searchQuery: '',
})

const fetchFavorites = async () => {
  try {
    const { data } = await axios.get(`https://2fdce0137fa86a1b.mokky.dev/favorites`)

    items.value = items.value.map((item) => {
      const favoriteItem = data.find((obj) => obj.id === item.id)

      if (!favoriteItem) {
        return item
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favoriteItem.id,
      }
    })
  } catch (error) {
    console.log(error)
  }
}

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    }

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }

    const { data } = await axios.get(`https://2fdce0137fa86a1b.mokky.dev/items`, {
      params,
    })

    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      isAdded: false,
    }))
  } catch (error) {
    console.log(error)
  }
}

onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})
watch(filters, fetchItems)
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-10">Все кроссовки</h2>

        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
            <option value="name">По названию</option>
            <option value="price">По цене (по убыванию)</option>
            <option value="-price">По цене (по возрастанию)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="" />
            <input
              @input="onChangeSearchInput"
              placeholder="Поиск..."
              class="border rounded-md py-2 pl-12 pr-4 outline-none focus:border-gray-400"
            />
          </div>
        </div>
      </div>

      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>
