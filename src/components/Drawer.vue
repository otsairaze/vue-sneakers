<script setup>
import DrawerHeader from './DrawerHeader.vue'
import CartItem from './CartItem.vue'
</script>

<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70" />
  <div class="bg-white w-96 h-full bg-white fixed right-0 top-0 z-20 p-8">
    <DrawerHeader />
    <CartItem />
  </div>
</template>
