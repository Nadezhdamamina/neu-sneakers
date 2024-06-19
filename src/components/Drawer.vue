<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
</script>

<template>
  <div class="fixed z-10 top-0 h-full w-full bg-black opacity-70"></div>
  <div
    class="flex flex-col justify-between fixed h-full z-10 top-0 h-full right-0 w-96 bg-white px-10 py-7"
  >
    <DrawerHead />
    <div class="flex flex-col flex-1 justify-between">
      <CartItemList />

      <!-- <div> -->
      <div class="flex flex-col gap-4 mt-7">
        <div class="flex items-end gap-2">
          <span>Итого:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <span class="font-bold">1000 руб.</span>
        </div>

        <div class="flex items-end gap-2">
          <span>Налог 5%:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <span class="font-bold">50 руб.</span>
        </div>

        <button
          disabled=""
          class="flex justify-center items-center gap-3 w-full py-3 mt-10 bg-lime-500 text-white disabled:bg-slate-300 rounded-xl transition active:bg-lime-700 hover:bg-lime-600 cursor:pointer"
        >
          Оформить заказ
          <img src="/arrow-next.svg" alt="Arrow" />
        </button>
      </div>
    </div>
  </div>
  <!-- </div> -->
</template>
