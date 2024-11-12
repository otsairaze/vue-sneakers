<script setup>
import DrawerHeader from './DrawerHeader.vue'
import CartItemList from './CartItemList.vue'
</script>

<template>
  <div class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70" />
  <div class="bg-white w-96 h-full bg-white fixed right-0 top-0 z-20 p-8">
    <DrawerHeader />

    <CartItemList />

    <div class="flex flex-col gap-4 mt-7">
      <div class="flex gap-2">
        <span>Итого:</span>
        <div class="flex-1 border-b border-dashed" />
        <b>21 498 руб. </b>
      </div>

      <div class="flex gap-2">
        <span>Налог 5%:</span>
        <div class="flex-1 border-b border-dashed" />
        <b>1299 руб. </b>
      </div>

      <button
        class="mt-7 bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 transition active:bg-lime-700 cursor pointer"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
