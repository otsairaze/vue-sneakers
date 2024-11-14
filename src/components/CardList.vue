<script setup>
import Card from './Card.vue'
defineProps({
  items: Array,
  isFavorite: Boolean,
})

const emit = defineEmits(['addToFavorite', 'addToCart'])

const onClickAdd = () => {
  emit('addToFavorite')
}
</script>

<template>
  <div class="grid grid-cols-4 gap-10">
    <Card
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :image-url="item.imageUrl"
      :price="item.price"
      :onClickAdd="() => emit('addToCart', item)"
      :onClickFavorite="() => emit('addToFavorite', item)"
      :is-favorite="item.isFavorite"
      :is-added="item.isAdded"
    />
  </div>
</template>
