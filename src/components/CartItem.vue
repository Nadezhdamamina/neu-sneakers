<script setup>
defineProps({
  id: Number,
  imageUrl: String,
  title: String,
  price: Number
  // isFavorite: Boolean,
  // isAdded: Boolean,
  // onClicKFavorite: Function,
  // onClickAdd: Function,
  // onClickDelete: Function
})
</script>

<template>
  <div class="relative flex items-center w-full border border-slate-200 rounded-xl p-4 gap-4">
    <img :src="imageUrl" class="w-16 h-16" :alt="title" />
    <div class="flex flex-col w-full flex-1">
      <p>{{ title }}</p>
      <div class="flex justify-between mt-5">
        <span class="flex-1 font-bold">{{ price }} руб.</span>
        <img
          class="cursor-pointer opacity-30 hover:opacity-100 transition"
          src="/close.svg"
          alt="Close"
        />
      </div>
    </div>
  </div>
</template>
