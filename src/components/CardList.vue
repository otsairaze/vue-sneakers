<script setup>
import Card from './Card.vue'
defineProps({
  items: Array,
})

const onClickAdd = () => {
  alert('Добавить')
}
</script>

<template>
  <div class="grid grid-cols-4 gap-10">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :image-url="item.imageUrl"
      :price="item.price"
      :is-favorite="true"
    />
  </div>
</template>
