<script setup>
import axios from 'axios'
import { ref, computed, inject } from 'vue'

import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
// import InfoBlock from './InfoBlock.vue'

const props = defineProps({
  totalPrice: Number,
  vatPrice: Number
})

const { cart, closeDrawer } = inject('cart')

const isCreating = ref(false)
const orderId = ref(null)

const createOrder = async () => {
  try {
    isCreating.value = true

    const { data } = await axios.post(`https://db603569a6b95760.mokky.dev/orders`, {
      items: cart.value,
      totalPrice: props.totalPrice.value
    })

    cart.value = []

    orderId.value = data.id
  } catch (err) {
    console.log(err)
  } finally {
    isCreating.value = false
  }
}

const cartIsEmpty = computed(() => cart.value.length === 0)
const buttonDisabled = computed(() => isCreating.value || cartIsEmpty.value)
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
          <span class="font-bold"> {{ totalPrice }} руб. </span>
        </div>

        <div class="flex items-end gap-2">
          <span>Налог 5%:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <span class="font-bold"> {{ vatPrice }} руб.</span>
        </div>

        <button
          :disabled="buttonDisabled"
          @click="createOrder"
          class="mt-4 transition bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 cursor-pointer"
        >
          Оформить заказ
          <!-- <img src="/arrow-next.svg" alt="Arrow" /> -->
        </button>
      </div>
    </div>
  </div>
  <!-- </div> -->
</template>
