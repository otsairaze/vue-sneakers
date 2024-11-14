<script setup>
import { inject } from 'vue'
import CartItem from './CartItem.vue'

const { cart } = inject('cart')
</script>

<template>
  <div class="flex flex-col flex-1 gap-4">
    <CartItem v-for="item in cart" :key="item.id" />
  </div>
</template>
