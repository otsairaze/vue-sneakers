<script setup>
import Card from './Card.vue'

const onClickAdd = () => {
  alert('Добавить')
}
</script>

<template>
  <div class="grid grid-cols-4 gap-10">
    <Card
      image-url="/sneakers/sneakers-2.jpg"
      title="Мужские Кроссовки Nike Blazer Mid Suede"
      :price="12999"
      :is-added="true"
      :is-favorite="false"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
